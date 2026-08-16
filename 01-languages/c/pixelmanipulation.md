# Intro

Resolution. 320x200- popular resolution for oldass games back in msdos games. called `mode 13h`. VGA.

2d grid, and to access the pixel, we can just write it at the pixel positiom in monitor, and graphic driver will write it on the montior.

**framebuffer**

`uint32_t framebuffer[320 * 200];`

64000 pixel positions, if we think linearly.

then `put_pixel(30, 60, 0xFF0000);`, 30 is x coordinate, 60 is y coordinate, and the hexadecimal is the colior.

But now this cannot happen nowadays directly. Because protection layer like OSes protect these.

So we cannot in windows, mac or Linux. So this is a problem. So we have to do specific code for specific OSes, according to the access provided by libraries. But it becomes complicated.

So we need a lib, to target for the specific hardware. Cross-platform. **SDL**.

CODE DUMPS;

```c


#include<SDL3/SDL.h>
#include<stdio.h>
#include<stdlib.h>

int main(void){

    SDL_Init(SDL_INIT_VIDEO);
    printf("Hello, SDL");
    return EXIT_SUCCESS;
}
```

```
/usr/bin/ld: /tmp/ccbaSlGZ.o: in function `main':
main.c:(.text+0xe): undefined reference to `SDL_Init'
collect2: error: ld returned 1 exit status
```
gives error because compiler cannot identify the path.

the ld, means it gives a linker problem.

```bash
gcc main.c `pkg-config --cflags sdl3` `pkg-config --libs sdl3` -o framebuffer
```

we use this to compile. and put this in a makefile to make it easier.

`uint32_t framebuffer[WIDTH*HEIGHT];`, why not use directly int, because we dont know if its in 32 bit or not. 4x32 bit, so there is no exact size of int in bits, it says atleast 16bits, so we do unsigned int, we include <stdint.h> to guarrantee 32 bits.

```c
#include<SDL3/SDL.h>
#include<stdio.h>
#include<stdlib.h>
#include<stdint.h>

#define WIDTH 320
#define HEIGHT 200

uint32_t framebuffer[WIDTH*HEIGHT];

int main(void){

    SDL_Init(SDL_INIT_VIDEO);
    printf("Hello, SDL");
    return EXIT_SUCCESS;
}
```
SDL documentation to know more.

```c
#include<SDL3/SDL.h>
#include<stdio.h>
#include<stdlib.h>
#include<stdint.h>

#define WIDTH 320
#define HEIGHT 200

uint32_t framebuffer[WIDTH*HEIGHT];

int main(void){
    SDL_Window *window;
    SDL_Renderer *renderer;
    SDL_Texture *texture;

    SDL_Init(SDL_INIT_VIDEO);
    
    window = SDL_CreateWindow(
        "SDL Framebuffer",
        WIDTH,
        HEIGHT,
        0
    );

    renderer = SDL_CreateRenderer(
        window,
        NULL
    );

    texture = SDL_CreateTexture(
        renderer,
        SDL_PIXELFORMAT_XRGB8888,
        SDL_TEXTUREACCESS_STREAMING,
        WIDTH,
        HEIGHT
    );

    while(true){
    /*Display window and renderer*/

    SDL_RenderClear(renderer);
    SDL_RenderPresent(renderer);
    }
    
 
    return EXIT_SUCCESS;
}
```

the window becomes irresponsive, because user is not able to do anything.

ADDDING POLLING EVENTS

```c
#include<SDL3/SDL.h>
#include<stdio.h>
#include<stdlib.h>
#include<stdint.h>

#define WIDTH 320
#define HEIGHT 200

uint32_t framebuffer[WIDTH*HEIGHT];

int main(void){
    SDL_Window *window;
    SDL_Renderer *renderer;
    SDL_Texture *texture;
    SDL_Event event;

    SDL_Init(SDL_INIT_VIDEO);
    
    window = SDL_CreateWindow(
        "SDL Framebuffer",
        WIDTH,
        HEIGHT,
        0
    );

    renderer = SDL_CreateRenderer(
        window,
        NULL
    );

    texture = SDL_CreateTexture(
        renderer,
        SDL_PIXELFORMAT_XRGB8888,
        SDL_TEXTUREACCESS_STREAMING,
        WIDTH,
        HEIGHT
    );

    uint8_t is_running = 1;

    while(is_running){

    /*Poll the events, like keyboard inputs or close button etc*/
    while(SDL_PollEvent(&event)){
        if(event.type == SDL_EVENT_QUIT){
            is_running =0;
        }
    }
    /*Display window and renderer*/

    SDL_RenderClear(renderer);
    SDL_RenderPresent(renderer);
    }
    
    SDL_DestroyTexture(texture);
    SDL_DestroyRenderer(renderer);
    SDL_DestroyWindow(window);

    SDL_Quit();

    return EXIT_SUCCESS;
}
```

```c
#include<SDL3/SDL.h>
#include<stdio.h>
#include<stdlib.h>
#include<stdint.h>

#define WIDTH 320
#define HEIGHT 200

uint32_t framebuffer[WIDTH*HEIGHT];

int main(void){
    SDL_Window *window;
    SDL_Renderer *renderer;
    SDL_Texture *texture;
    SDL_Event event;

    SDL_Init(SDL_INIT_VIDEO);
    
    window = SDL_CreateWindow(
        "SDL Framebuffer",
        WIDTH,
        HEIGHT,
        0
    );

    renderer = SDL_CreateRenderer(
        window,
        NULL
    );

    texture = SDL_CreateTexture(
        renderer,
        SDL_PIXELFORMAT_XRGB8888,
        SDL_TEXTUREACCESS_STREAMING,
        WIDTH,
        HEIGHT
    );

    uint8_t is_running = 1;

    while(is_running){

    /*Poll the events, like keyboard inputs or close button etc*/
    while(SDL_PollEvent(&event)){
        if(event.type == SDL_EVENT_QUIT){
            is_running = 0;
        }
    }

    /*here we manipulate our framebuffer*/
    framebuffer[16500] = 0xFF0000;

    /* coopy the contentes of framebuffer to the texture*/
    SDL_UpdateTexture(
        texture,
        NULL,
        framebuffer,
        //PITCH:THE WIDTH OF TEXTURE IN BYTES
        WIDTH * sizeof(uint32_t)
    );
    /*Display window and renderer*/

    SDL_RenderClear(renderer);
    SDL_RenderTexture(renderer, texture, NULL, NULL);
    SDL_RenderPresent(renderer);
    }
    
    SDL_DestroyTexture(texture);
    SDL_DestroyRenderer(renderer);
    SDL_DestroyWindow(window);

    SDL_Quit();

    return EXIT_SUCCESS;
}
```

below added window resizing.

```
#include<SDL3/SDL.h>
#include<stdio.h>
#include<stdlib.h>
#include<stdint.h>

#define WIDTH 320
#define HEIGHT 200

uint32_t framebuffer[WIDTH*HEIGHT];

int main(void){
    SDL_Window *window;
    SDL_Renderer *renderer;
    SDL_Texture *texture;
    SDL_Event event;

    SDL_Init(SDL_INIT_VIDEO);
    
    window = SDL_CreateWindow(
        "SDL Framebuffer",
        WIDTH * 4,
        HEIGHT * 4,
        0
    );

    renderer = SDL_CreateRenderer(
        window,
        NULL
    );

    texture = SDL_CreateTexture(
        renderer,
        SDL_PIXELFORMAT_XRGB8888,
        SDL_TEXTUREACCESS_STREAMING,
        WIDTH,
        HEIGHT
    );

    //how it scales

    SDL_SetTextureScaleMode(texture, SDL_SCALEMODE_NEAREST);
    uint8_t is_running = 1;

    while(is_running){

    /*Poll the events, like keyboard inputs or close button etc*/
    while(SDL_PollEvent(&event)){
        if(event.type == SDL_EVENT_QUIT){
            is_running = 0;
        }
    }

    /*here we manipulate our framebuffer*/
    framebuffer[16500] = 0xFF0000;

    /* coopy the contentes of framebuffer to the texture*/
    SDL_UpdateTexture(
        texture,
        NULL,
        framebuffer,
        //PITCH:THE WIDTH OF TEXTURE IN BYTES
        WIDTH * sizeof(uint32_t)
    );
    /*Display window and renderer*/

    SDL_RenderClear(renderer);
    SDL_RenderTexture(renderer, texture, NULL, NULL);
    SDL_RenderPresent(renderer);
    }
    
    SDL_DestroyTexture(texture);
    SDL_DestroyRenderer(renderer);
    SDL_DestroyWindow(window);

    SDL_Quit();

    return EXIT_SUCCESS;
}
```

SDL init can return negative no. if eror is forund.

below we did error handling.

```c
//read documentation to understand functions

#include<SDL3/SDL.h>
#include<stdio.h>
#include<stdlib.h>
#include<stdint.h>

#define WIDTH 320
#define HEIGHT 200

uint32_t framebuffer[WIDTH*HEIGHT];

int main(void){
    SDL_Window *window;
    SDL_Renderer *renderer;
    SDL_Texture *texture;
    SDL_Event event;

    if(!SDL_Init(SDL_INIT_VIDEO)) {
        fprintf(stderr, "SDL INIT failed:%s\n", SDL_GetError());
        return EXIT_FAILURE;
    }

    
    window = SDL_CreateWindow(
        "SDL Framebuffer",
        WIDTH * 4,
        HEIGHT * 4,
        0
    );

    if(window == NULL){
        fprintf(stderr, "SDL_CreateWindow FAILED:%s\n", SDL_GetError());
        SDL_Quit();
        //to undo the above sdl init.

        return EXIT_FAILURE;
    }

    renderer = SDL_CreateRenderer(
        window,
        NULL
    );

    if(renderer == NULL){
        fprintf(stderr, "SDL_CreateRenderer FAILED:%s\n", SDL_GetError());
        SDL_DestroyWindow(window);
        SDL_Quit;
        //as init and window bother may get created.

    }
    texture = SDL_CreateTexture(
        renderer,
        SDL_PIXELFORMAT_XRGB8888,
        SDL_TEXTUREACCESS_STREAMING,
        WIDTH,
        HEIGHT
    );

    if(texture == NULL){
        fprintf(stderr, "SDL_CreateTexture FAILED:%s\n", SDL_GetError());
        SDL_DestroyRenderer(renderer);
        SDL_DestroyWindow(window);
        SDL_Quit();
    }
    //how it scales

    SDL_SetTextureScaleMode(texture, SDL_SCALEMODE_NEAREST);
    uint8_t is_running = 1;

    while(is_running){

    /*Poll the events, like keyboard inputs or close button etc*/
    while(SDL_PollEvent(&event)){
        if(event.type == SDL_EVENT_QUIT){
            is_running = 0;
        }
    }

    /*here we manipulate our framebuffer*/
    framebuffer[16500] = 0xFF0000;

    /* coopy the contentes of framebuffer to the texture*/
    SDL_UpdateTexture(
        texture,
        NULL,
        framebuffer,
        //PITCH:THE WIDTH OF TEXTURE IN BYTES
        WIDTH * sizeof(uint32_t)
    );
    /*Display window and renderer*/

    SDL_RenderClear(renderer);
    SDL_RenderTexture(renderer, texture, NULL, NULL);
    SDL_RenderPresent(renderer);
    }
    
    SDL_DestroyTexture(texture);
    SDL_DestroyRenderer(renderer);
    SDL_DestroyWindow(window);

    SDL_Quit();

    return EXIT_SUCCESS;
}
```

Now we use put_pixel function to manipulate acc to coordinates.

we want to imagine it as 2d grid, but in reality its contiguous.

so when x = 60 and y = 30

320 x 30 + 60. This is how we make 1d, from 2d.

putting put_pixel functions.

```c
//read documentation to understand functions

#include<SDL3/SDL.h>
#include<stdio.h>
#include<stdlib.h>
#include<stdint.h>

#define WIDTH 320
#define HEIGHT 200

uint32_t framebuffer[WIDTH*HEIGHT];

void put_pixel(int x, int y, uint32_t color){
    //Todo: converting x and y into array-index

    framebuffer[WIDTH*y + x] = color;
`
}

int main(void){
    SDL_Window *window;
    SDL_Renderer *renderer;
    SDL_Texture *texture;
    SDL_Event event;

    if(!SDL_Init(SDL_INIT_VIDEO)) {
        fprintf(stderr, "SDL INIT failed:%s\n", SDL_GetError());
        return EXIT_FAILURE;
    }

    
    window = SDL_CreateWindow(
        "SDL Framebuffer",
        WIDTH * 4,
        HEIGHT * 4,
        0
    );

    if(window == NULL){
        fprintf(stderr, "SDL_CreateWindow FAILED:%s\n", SDL_GetError());
        SDL_Quit();
        //to undo the above sdl init.

        return EXIT_FAILURE;
    }

    renderer = SDL_CreateRenderer(
        window,
        NULL
    );

    if(renderer == NULL){
        fprintf(stderr, "SDL_CreateRenderer FAILED:%s\n", SDL_GetError());
        SDL_DestroyWindow(window);
        SDL_Quit;
        //as init and window bother may get created.

    }
    texture = SDL_CreateTexture(
        renderer,
        SDL_PIXELFORMAT_XRGB8888,
        SDL_TEXTUREACCESS_STREAMING,
        WIDTH,
        HEIGHT
    );

    if(texture == NULL){
        fprintf(stderr, "SDL_CreateTexture FAILED:%s\n", SDL_GetError());
        SDL_DestroyRenderer(renderer);
        SDL_DestroyWindow(window);
        SDL_Quit();
    }
    //how it scales

    SDL_SetTextureScaleMode(texture, SDL_SCALEMODE_NEAREST);
    uint8_t is_running = 1;

    while(is_running){

    /*Poll the events, like keyboard inputs or close button etc*/
    while(SDL_PollEvent(&event)){
        if(event.type == SDL_EVENT_QUIT){
            is_running = 0;
        }
    }

    /*here we manipulate our framebuffer*/
    put_pixel(WIDTH/2, HEIGHT/2, 0xFF0000);

    /* coopy the contentes of framebuffer to the texture*/
    SDL_UpdateTexture(
        texture,
        NULL,
        framebuffer,
        //PITCH:THE WIDTH OF TEXTURE IN BYTES
        WIDTH * sizeof(uint32_t)
    );
    /*Display window and renderer*/

    SDL_RenderClear(renderer);
    SDL_RenderTexture(renderer, texture, NULL, NULL);
    SDL_RenderPresent(renderer);
    }
    
    SDL_DestroyTexture(texture);
    SDL_DestroyRenderer(renderer);
    SDL_DestroyWindow(window);

    SDL_Quit();

    return EXIT_SUCCESS;
}
```

We want to make it kind of animation. like 60fps or etc to update the texture.

capping framerate

```c
//read documentation to understand functions

#include<SDL3/SDL.h>
#include<stdio.h>
#include<stdlib.h>
#include<stdint.h>

#define WIDTH 320
#define HEIGHT 200

uint32_t framebuffer[WIDTH*HEIGHT];

void put_pixel(int x, int y, uint32_t color){
    //Todo: converting x and y into array-index

    framebuffer[WIDTH*y + x] = color;

}

int main(void){
    SDL_Window *window;
    SDL_Renderer *renderer;
    SDL_Texture *texture;
    SDL_Event event;

    const double target_frame = 1.0/60.0; // each frame should be running at 0.016s

    if(!SDL_Init(SDL_INIT_VIDEO)) {
        fprintf(stderr, "SDL INIT failed:%s\n", SDL_GetError());
        return EXIT_FAILURE;
    }

    
    window = SDL_CreateWindow(
        "SDL Framebuffer",
        WIDTH * 4,
        HEIGHT * 4,
        0
    );

    if(window == NULL){
        fprintf(stderr, "SDL_CreateWindow FAILED:%s\n", SDL_GetError());
        SDL_Quit();
        //to undo the above sdl init.

        return EXIT_FAILURE;
    }

    renderer = SDL_CreateRenderer(
        window,
        NULL
    );

    if(renderer == NULL){
        fprintf(stderr, "SDL_CreateRenderer FAILED:%s\n", SDL_GetError());
        SDL_DestroyWindow(window);
        SDL_Quit;
        //as init and window bother may get created.

    }
    texture = SDL_CreateTexture(
        renderer,
        SDL_PIXELFORMAT_XRGB8888,
        SDL_TEXTUREACCESS_STREAMING,
        WIDTH,
        HEIGHT
    );

    if(texture == NULL){
        fprintf(stderr, "SDL_CreateTexture FAILED:%s\n", SDL_GetError());
        SDL_DestroyRenderer(renderer);
        SDL_DestroyWindow(window);
        SDL_Quit();
    }
    //how it scales

    SDL_SetTextureScaleMode(texture, SDL_SCALEMODE_NEAREST);
    uint8_t is_running = 1;

    while(is_running){
        uint64_t start = SDL_GetPerformanceCounter();//gives microsecond level precision

    /*Poll the events, like keyboard inputs or close button etc*/
    while(SDL_PollEvent(&event)){
        if(event.type == SDL_EVENT_QUIT){
            is_running = 0;
        }
    }

    /*here we manipulate our framebuffer*/
    put_pixel(WIDTH/2, HEIGHT/2, 0xFF0000);

    /* coopy the contentes of framebuffer to the texture*/
    SDL_UpdateTexture(
        texture,
        NULL,
        framebuffer,
        //PITCH:THE WIDTH OF TEXTURE IN BYTES
        WIDTH * sizeof(uint32_t)
    );
    /*Display window and renderer*/

    SDL_RenderClear(renderer);
    SDL_RenderTexture(renderer, texture, NULL, NULL);
    SDL_RenderPresent(renderer);
    
    uint64_t end = SDL_GetPerformanceCounter();

    double elapsed = (double)(end - start)/ (double)SDL_GetPerformanceFrequency();

    //caping the framerate to 60 fps

    if(elapsed<target_frame){
        SDL_Delay((target_frame - elapsed) * 1000.0); //sleep for a while till we reach 60 fps.
    }

}
    
    SDL_DestroyTexture(texture);
    SDL_DestroyRenderer(renderer);
    SDL_DestroyWindow(window);

    SDL_Quit();

    return EXIT_SUCCESS;
}
```

adding a loop for multiple pixels

```c
//read documentation to understand functions

#include<SDL3/SDL.h>
#include<stdio.h>
#include<stdlib.h>
#include<stdint.h>

#define WIDTH 320
#define HEIGHT 200

uint32_t framebuffer[WIDTH*HEIGHT];

void put_pixel(int x, int y, uint32_t color){
    //Todo: converting x and y into array-index

    framebuffer[WIDTH*y + x] = color;

}

int main(void){
    SDL_Window *window;
    SDL_Renderer *renderer;
    SDL_Texture *texture;
    SDL_Event event;

    const double target_frame = 1.0/60.0; // each frame should be running at 0.016s

    if(!SDL_Init(SDL_INIT_VIDEO)) {
        fprintf(stderr, "SDL INIT failed:%s\n", SDL_GetError());
        return EXIT_FAILURE;
    }

    
    window = SDL_CreateWindow(
        "SDL Framebuffer",
        WIDTH * 4,
        HEIGHT * 4,
        0
    );

    if(window == NULL){
        fprintf(stderr, "SDL_CreateWindow FAILED:%s\n", SDL_GetError());
        SDL_Quit();
        //to undo the above sdl init.

        return EXIT_FAILURE;
    }

    renderer = SDL_CreateRenderer(
        window,
        NULL
    );

    if(renderer == NULL){
        fprintf(stderr, "SDL_CreateRenderer FAILED:%s\n", SDL_GetError());
        SDL_DestroyWindow(window);
        SDL_Quit;
        //as init and window bother may get created.

    }
    texture = SDL_CreateTexture(
        renderer,
        SDL_PIXELFORMAT_XRGB8888,
        SDL_TEXTUREACCESS_STREAMING,
        WIDTH,
        HEIGHT
    );

    if(texture == NULL){
        fprintf(stderr, "SDL_CreateTexture FAILED:%s\n", SDL_GetError());
        SDL_DestroyRenderer(renderer);
        SDL_DestroyWindow(window);
        SDL_Quit();
    }
    //how it scales

    SDL_SetTextureScaleMode(texture, SDL_SCALEMODE_NEAREST);
    uint8_t is_running = 1;

    while(is_running){
        uint64_t start = SDL_GetPerformanceCounter();//gives microsecond level precision

    /*Poll the events, like keyboard inputs or close button etc*/
    while(SDL_PollEvent(&event)){
        if(event.type == SDL_EVENT_QUIT){
            is_running = 0;
        }
    }

    /*here we manipulate our framebuffer*/
    for(int y = 0; y < HEIGHT; y++){
        for(int x = 0; x < WIDTH; x++){
            if(x % 5 == 0){
                put_pixel(x, y, 0x00FFFF);
            }
        }
    }

    /* coopy the contentes of framebuffer to the texture*/
    SDL_UpdateTexture(
        texture,
        NULL,
        framebuffer,
        //PITCH:THE WIDTH OF TEXTURE IN BYTES
        WIDTH * sizeof(uint32_t)
    );
    /*Display window and renderer*/

    SDL_RenderClear(renderer);
    SDL_RenderTexture(renderer, texture, NULL, NULL);
    SDL_RenderPresent(renderer);
    
    uint64_t end = SDL_GetPerformanceCounter();

    double elapsed = (double)(end - start)/ (double)SDL_GetPerformanceFrequency();

    //caping the framerate to 60 fps

    if(elapsed<target_frame){
        SDL_Delay((target_frame - elapsed) * 1000.0); //sleep for a while till we reach 60 fps.
    }

}
    
    SDL_DestroyTexture(texture);
    SDL_DestroyRenderer(renderer);
    SDL_DestroyWindow(window);

    SDL_Quit();

    return EXIT_SUCCESS;
}
```

clearing with a color and adding error cases for x and y

```c
//read documentation to understand functions

#include<SDL3/SDL.h>
#include<stdio.h>
#include<stdlib.h>
#include<stdint.h>

#define WIDTH 320
#define HEIGHT 200

uint32_t framebuffer[WIDTH*HEIGHT];

void put_pixel(int x, int y, uint32_t color){
    //Todo: converting x and y into array-index
    if(x < 0 || x >= WIDTH || y < 0 || y >= HEIGHT){
        return;
    }
    framebuffer[WIDTH*y + x] = color;

}

void clear(uint32_t color){
    for(int i = 0; i<WIDTH * HEIGHT; i++){
        framebuffer[i] = color;
    }
}
int main(void){
    SDL_Window *window;
    SDL_Renderer *renderer;
    SDL_Texture *texture;
    SDL_Event event;

    const double target_frame = 1.0/60.0; // each frame should be running at 0.016s

    if(!SDL_Init(SDL_INIT_VIDEO)) {
        fprintf(stderr, "SDL INIT failed:%s\n", SDL_GetError());
        return EXIT_FAILURE;
    }

    
    window = SDL_CreateWindow(
        "SDL Framebuffer",
        WIDTH * 4,
        HEIGHT * 4,
        0
    );

    if(window == NULL){
        fprintf(stderr, "SDL_CreateWindow FAILED:%s\n", SDL_GetError());
        SDL_Quit();
        //to undo the above sdl init.

        return EXIT_FAILURE;
    }

    renderer = SDL_CreateRenderer(
        window,
        NULL
    );

    if(renderer == NULL){
        fprintf(stderr, "SDL_CreateRenderer FAILED:%s\n", SDL_GetError());
        SDL_DestroyWindow(window);
        SDL_Quit;
        //as init and window bother may get created.

    }
    texture = SDL_CreateTexture(
        renderer,
        SDL_PIXELFORMAT_XRGB8888,
        SDL_TEXTUREACCESS_STREAMING,
        WIDTH,
        HEIGHT
    );

    if(texture == NULL){
        fprintf(stderr, "SDL_CreateTexture FAILED:%s\n", SDL_GetError());
        SDL_DestroyRenderer(renderer);
        SDL_DestroyWindow(window);
        SDL_Quit();
    }
    //how it scales

    SDL_SetTextureScaleMode(texture, SDL_SCALEMODE_NEAREST);
    uint8_t is_running = 1;

    while(is_running){
        uint64_t start = SDL_GetPerformanceCounter();//gives microsecond level precision

    /*Poll the events, like keyboard inputs or close button etc*/
    while(SDL_PollEvent(&event)){
        if(event.type == SDL_EVENT_QUIT){
            is_running = 0;
        }
    }

    clear(0xFFFFFF);
    /*here we manipulate our framebuffer*/
    for(int y = 0; y < HEIGHT; y++){
        for(int x = 0; x < WIDTH; x++){
            if(x % 5 == 0){
                put_pixel(x, y, 0x00FFFF);
            }
        }
    }

    /* coopy the contentes of framebuffer to the texture*/
    SDL_UpdateTexture(
        texture,
        NULL,
        framebuffer,
        //PITCH:THE WIDTH OF TEXTURE IN BYTES
        WIDTH * sizeof(uint32_t)
    );
    /*Display window and renderer*/

    SDL_RenderClear(renderer);
    SDL_RenderTexture(renderer, texture, NULL, NULL);
    SDL_RenderPresent(renderer);
    
    uint64_t end = SDL_GetPerformanceCounter();

    double elapsed = (double)(end - start)/ (double)SDL_GetPerformanceFrequency();

    //caping the framerate to 60 fps

    if(elapsed<target_frame){
        SDL_Delay((target_frame - elapsed) * 1000.0); //sleep for a while till we reach 60 fps.
    }

}
    
    SDL_DestroyTexture(texture);
    SDL_DestroyRenderer(renderer);
    SDL_DestroyWindow(window);

    SDL_Quit();

    return EXIT_SUCCESS;
}
```

addING ANIMATIONS AND FRAMES

```C
//read documentation to understand functions

#include<SDL3/SDL.h>
#include<stdio.h>
#include<stdlib.h>
#include<stdint.h>

#define WIDTH 320
#define HEIGHT 200

uint32_t framebuffer[WIDTH*HEIGHT];

void put_pixel(int x, int y, uint32_t color){
    //Todo: converting x and y into array-index
    if(x < 0 || x >= WIDTH || y < 0 || y >= HEIGHT){
        return;
    }
    framebuffer[WIDTH*y + x] = color;

}

void clear(uint32_t color){
    for(int i = 0; i<WIDTH * HEIGHT; i++){
        framebuffer[i] = color;
    }
}
int main(void){
    SDL_Window *window;
    SDL_Renderer *renderer;
    SDL_Texture *texture;
    SDL_Event event;

    const double target_frame = 1.0/60.0; // each frame should be running at 0.016s

    if(!SDL_Init(SDL_INIT_VIDEO)) {
        fprintf(stderr, "SDL INIT failed:%s\n", SDL_GetError());
        return EXIT_FAILURE;
    }

    
    window = SDL_CreateWindow(
        "SDL Framebuffer",
        WIDTH * 4,
        HEIGHT * 4,
        0
    );

    if(window == NULL){
        fprintf(stderr, "SDL_CreateWindow FAILED:%s\n", SDL_GetError());
        SDL_Quit();
        //to undo the above sdl init.

        return EXIT_FAILURE;
    }

    renderer = SDL_CreateRenderer(
        window,
        NULL
    );

    if(renderer == NULL){
        fprintf(stderr, "SDL_CreateRenderer FAILED:%s\n", SDL_GetError());
        SDL_DestroyWindow(window);
        SDL_Quit;
        //as init and window bother may get created.

    }
    texture = SDL_CreateTexture(
        renderer,
        SDL_PIXELFORMAT_XRGB8888,
        SDL_TEXTUREACCESS_STREAMING,
        WIDTH,
        HEIGHT
    );

    if(texture == NULL){
        fprintf(stderr, "SDL_CreateTexture FAILED:%s\n", SDL_GetError());
        SDL_DestroyRenderer(renderer);
        SDL_DestroyWindow(window);
        SDL_Quit();
    }
    //how it scales

    SDL_SetTextureScaleMode(texture, SDL_SCALEMODE_NEAREST);
    uint8_t is_running = 1;
    uint32_t frame = 0;

    while(is_running){
        uint64_t start = SDL_GetPerformanceCounter();//gives microsecond level precision

    /*Poll the events, like keyboard inputs or close button etc*/
    while(SDL_PollEvent(&event)){
        if(event.type == SDL_EVENT_QUIT){
            is_running = 0;
        }
    }

    clear(0x2A2A2A);
    /*here we manipulate our framebuffer*/
    int x = frame % 320;
    int y = HEIGHT/2;
    put_pixel(x, y, 0x00FFFF);

    /* coopy the contentes of framebuffer to the texture*/
    SDL_UpdateTexture(
        texture,
        NULL,
        framebuffer,
        //PITCH:THE WIDTH OF TEXTURE IN BYTES
        WIDTH * sizeof(uint32_t)
    );
    /*Display window and renderer*/

    SDL_RenderClear(renderer);
    SDL_RenderTexture(renderer, texture, NULL, NULL);
    SDL_RenderPresent(renderer);
    
    uint64_t end = SDL_GetPerformanceCounter();

    double elapsed = (double)(end - start)/ (double)SDL_GetPerformanceFrequency();

    //caping the framerate to 60 fps

    if(elapsed<target_frame){
        SDL_Delay((target_frame - elapsed) * 1000.0); //sleep for a while till we reach 60 fps.
    }
    frame+=1;
}
    
    SDL_DestroyTexture(texture);
    SDL_DestroyRenderer(renderer);
    SDL_DestroyWindow(window);

    SDL_Quit();

    return EXIT_SUCCESS;
}
```

This whole process is done in CPU rendering, not GPU stuff and CPU executes this linearly, but GPU can perform these tiny processes parallely. So we did was software rendering.

### THe doom fire effect

```c
#include <SDL3/SDL.h>
#include <stdio.h>
#include <stdlib.h>
#include "defs.h"

#define WIDTH 320
#define HEIGHT 240

static u32 framebuffer[WIDTH * HEIGHT];

/* Doom fire variables and color palette */
#define FIRE_W WIDTH
#define FIRE_H HEIGHT

#define FIRE_PALETTE_SIZE 37

static u8 fire_pixels[FIRE_W * FIRE_H];

static const u32 fire_palette[FIRE_PALETTE_SIZE] = {
  0x070707, 0x1F0707, 0x2F0F07, 0x470F07, 0x571707, 0x671F07, 0x771F07,
  0x8F2707, 0x9F2F07, 0xAF3F07, 0xBF4707, 0xC74707, 0xDF4F07, 0xDF5707,
  0xDF5707, 0xD75F07, 0xD75F07, 0xD7670F, 0xCF6F0F, 0xCF770F, 0xCF7F0F,
  0xCF8717, 0xC78717, 0xC78F17, 0xC7971F, 0xBF9F1F, 0xBF9F1F, 0xBFA727,
  0xBFA727, 0xBFAF2F, 0xB7AF2F, 0xB7B72F, 0xB7B737, 0xCFCF6F, 0xDFDF9F,
  0xEFEFC7, 0xFFFFFF
};

/* Draw a pixel in the framebuffer at 2D coordinates x and y */
void put_pixel(u32 x, u32 y, u32 color) {
  if (x < 0 || x >= WIDTH || y < 0 || y >= HEIGHT) {
    return;
  }
  framebuffer[y * WIDTH + x] = color;
}

/* Clear the entire framebuffer with a unique color */
void clear(u32 color) {
  for (u32 i = 0; i < WIDTH * HEIGHT; i++) {
    framebuffer[i] = color;
  }
}

/* Main function */
int main(void) {
  SDL_Window *window;
  SDL_Renderer *renderer;
  SDL_Texture *texture;
  SDL_Event event;

  const f64 target_frame = 1.0 / 60.0;

  if (!SDL_Init(SDL_INIT_VIDEO)) {
    fprintf(stderr, "SDL_Init failed: %s\n", SDL_GetError());
    return EXIT_FAILURE;
  }

  window = SDL_CreateWindow(
    "Framebuffer",
    WIDTH * 2,
    HEIGHT * 2,
    0
  );

  if (window == NULL) {
    fprintf(stderr, "SDL_CreateWindow failed: %s\n", SDL_GetError());
    SDL_Quit();
    return EXIT_FAILURE;
  }

  renderer = SDL_CreateRenderer(
    window,
    NULL
  );

  if (renderer == NULL) {
    fprintf(stderr, "SDL_CreateRenderer failed: %s\n", SDL_GetError());

    SDL_DestroyWindow(window);
    SDL_Quit();

    return EXIT_FAILURE;
  }

  texture = SDL_CreateTexture(
    renderer,
    SDL_PIXELFORMAT_XRGB8888,
    SDL_TEXTUREACCESS_STREAMING,
    WIDTH,
    HEIGHT
  );

  SDL_SetTextureScaleMode(texture, SDL_SCALEMODE_NEAREST);

  if (texture == NULL) {
    fprintf(stderr, "SDL_CreateTexture failed: %s\n", SDL_GetError());

    SDL_DestroyRenderer(renderer);
    SDL_DestroyWindow(window);
    SDL_Quit();

    return EXIT_FAILURE;
  }

  /* Fire initialization */
  for (int i = 0; i < FIRE_W * FIRE_H; i++) {
    fire_pixels[i] = 0;
  }

  /* Seed the fire bottom row with maximum intensity (this is the fire source) */
  for (int i = 0; i < FIRE_W; i++) {
    fire_pixels[(FIRE_H - 1) * FIRE_W + i] = FIRE_PALETTE_SIZE - 1;
  }

  u32 is_running = 1;
  u32 frame = 1;

  /* Frame loop */
  while (is_running) {
    u64 start = SDL_GetPerformanceCounter();

    /* Poll events */
    while (SDL_PollEvent(&event)) {
      if (event.type == SDL_EVENT_QUIT) {
        is_running = false;
      }
    }

    clear(0x000000);

    /* Fire update */
    for (u32 x = 0; x < FIRE_W; x++) {
      for (u32 y = 1; y < FIRE_H; y++) {
        u32 src = FIRE_W * y + x;
        u32 rand_idx = rand() % 4;
        i32 dst = (i32)src - FIRE_W;
        i32 dst_x = (i32)(src % FIRE_W) - (i32)rand_idx + 1;
        if (dst < 0 || dst_x < 0 || dst_x >= FIRE_W) {
          continue;
        } else {
          dst = dst - (i32)(src % FIRE_W) + dst_x;
          u8 src_val = fire_pixels[src];
          u8 decay = rand_idx & 1;
          fire_pixels[dst] = (src_val > decay) ? (src_val - decay) : 0;
        }
      }
    }

    /* Fire render */
    for (u32 y = 0; y < FIRE_H; y++) {
      for (u32 x = 0; x < FIRE_W; x++) {
        u8 idx = fire_pixels[y * FIRE_W + x];
        put_pixel(x, y, fire_palette[idx]);
      }
    }

    /* Copy contents of the framebuffer to our SDL texture */
    SDL_UpdateTexture(
      texture,
      NULL,
      framebuffer,
      WIDTH * sizeof(u32)
    );

    /* Render texture and display the renderer */
    SDL_RenderClear(renderer);
    SDL_RenderTexture(renderer, texture, NULL, NULL);
    SDL_RenderPresent(renderer);

    u64 end = SDL_GetPerformanceCounter();

    double elapsed = (double)(end - start) / (double)SDL_GetPerformanceFrequency();

    /* Cap the framerate to 60 FPS (16 milliseconds each frame) */
    if (elapsed < target_frame) {
      SDL_Delay((u32)((target_frame - elapsed) * 1000.0));
    }

    frame++;
  }

  /* Free all the SDL resources we created */
  SDL_DestroyTexture(texture);
  SDL_DestroyRenderer(renderer);
  SDL_DestroyWindow(window);
  SDL_Quit();

  return EXIT_SUCCESS;
}
```

Copy the previous one for the code made from scratch, then understand this.




## MY tinkerings

```c
    while(is_running){

        while(SDL_PollEvent(&event)){
            if(event.type == SDL_EVENT_QUIT){
                is_running = 0;
            }
        }
        SDL_RenderClear(renderer);
        SDL_RenderPresent(renderer);
    

    framebuffer[27000] = 0xFF0000;

    SDL_UpdateTexture(texture, NULL, framebuffer, WIDTH * sizeof(uint32_t));

    SDL_RenderClear(renderer);
    SDL_RenderTexture(renderer, texture, NULL, NULL);
    SDL_RenderPresent(renderer);
    }
    ```

    adding the renderclear and present just after the while and doing so again after updating texture, gives the blinking effect.
