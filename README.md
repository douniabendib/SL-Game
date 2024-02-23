<center><h1>SL Game</h1></center>
Description:
This project is a very small 2D game. Its purpose is to make you work with textures, sprites, and some other very basic gameplay elements.

Challenge:
Challenge is to develop a 2D game called "So Long" using the MiniLibX library. The game should involve a main character collecting all the collectibles on a map and then finding the shortest route to the map's exit. The player should be able to move the character using the W, A, S, and D keys, with movement restricted by walls. The game should display the current number of movements in the shell and have a 2D graphical representation using the MiniLibX library.
Final Project Blog Article: 
https://docs.google.com/document/d/1Oh1yUN4hmn4NOCC6Dx17VzFLnwnHpruz50Lo1QG-7p0/edit#heading=h.z6ne0og04bp5
LinkdIn:
https://www.linkedin.com/in/saliha-lammari-6611052b6/
https://www.linkedin.com/in/safae-sahih-b31228270/
https://www.linkedin.com/in/dounia-bendib-250212260/
mlx_init
SYN : void *mlx_init() DES : Creates connection between display and software. RTN : Returns void *identifier, used for further calls to the library routines. 2. mlx_new_window

SYN : void *mlx_new_window(void *mlx_ptr, int size_x, int size_y, char *title) DES : Creates a new windown on the screen, using the size_x and size_y parameters to determine its size, and title as the text that should be displayed in the window's title bar. The mlx_ptr parameter is the connection identifier returned by mlx_init(). RTN : If failes, return NULL. 3. mlx_clear_window

SYN : int mlx_clear_window(void *mlx_ptr, void *win_ptr) DES : clear (in black) the given window. mlx_ptr is the connection identifier, and win_ptr is a window identifier. RTN : Right now return nothing. 4. mlx_destroy_window

SYN : int mlx_destroy_window(void *mlx_ptr, void *win_ptr) DES : destroy the given window. mlx_ptr is the connection identifier, and win_ptr is a window identifier. RTN : Right now return nothing. 5. mlx_pixel_put

SYN : int mlx_pixel_put(void *mlx_ptr, void *win_ptr, int x, int y, int color)

DES : Draws a defined pixel in the window win_ptr using the (x, y) coordinates, and the specified color. The origin (0, 0) is the upper left corner of the window, the x and y axis respectively pointing right and down. The connection identifier, mlx_ptr, is needed.

color integer :

| 0 | R | G | B | +---+---+---+---+

mlx_string_put
SYN : int mlx_string_put(void *mlx_ptr, void *win_ptr, int x, int y, int color, char *string) DES : Same parameter with mlx_pixel_put. Instead of a simple pixel, the specified string will be displayed at (x, y). 7. mlx_new_image

SYN : void *mlx_new_image(void *mlx_ptr, int width, int height) DES : Creates a new image in memory. It only needs the size of the image to be created, using the width and height parameters, and the mlx_ptr connection identifier. RTN : Returns a void *identifier needed to manipulate this image later. 8. mlx_put_image_to_window

SYN : int mlx_put_image_to_window(void *mlx_ptr, void *win_ptr, void *img_ptr, int x, int y) DES : Can draw inside image, and can dump the image inside a specified window at any time to display it on the screen. Three identifiers are needed here, for the connection to the display, the window to use, and the image. The (x, y) coordinates define where the image should be placed in the window. 9. mlx_get_data_addr

SYN : char *mlx_get_data_addr(void *img_ptr, int *bits_per_pixel, int *size_line, int *endian) DES : The img_ptr parameter specifies the image to use. bits_per_pixel will be filled with the number of bits needed to represent a pixel color (also called the depth of the image). size_line is the number of bytes used to store one line of the image in memory. This information is needed to move from one line to another in the image. endian tells you wether the pixel color in the image needs to be stored in little endian (endian == 0), or big endian (endian == 1). RTN : Returns char *address that represents the begining of the memory area where the image is stored. From this adress, the first bits_per_pixel bits represent the color of the first pixel in the first line of the image. The second group of bits_per_pixel bits represent the second pixel of the first line, and so on. Add size_line to the adress to get the begining of the second line. You can reach any pixels of the image that way. 10. mlx_destroy_image

SYN : int mlx_destroy_image(void *mlx_ptr, void *img_ptr) DES : Destroys the given image(img_ptr). 11. mlx_get_color_value

SYN : unsigned int mlx_get_color_value(void *mlx_ptr, int color) DES : Depending on the display, the number of bits used to store a pixel color can change. The user usually represents a color in RGB mode, using one byte for each component. This must be translated to fit the bits_per_pixel requirement of the image, and make the color understandable to the graphical system. This function takes a standard RGB color parameter, and returns an unsigned int value. The bits_per_pixel least significant bits of this value can be stored int the image. 12. mlx_xpm_to_image & mlx_xpm_file_to_image

SYN : void *mlx_xpm_to_image(void *mlx_ptr, char **xpm_data, int *width, int *height) SYN : void *mlx_xpm_file_to_image(void *mlx_ptr, char **file_name, int *width, int *height) DES : Create a new image the same way. They will fill it using the specified xpm_data or filename, depending on which function is used. RTN : Return NULL if an error occurs. Otherwise return a non-null pointer as an image identifier. 13. mlx_loop

SYM : int mix_loop(void *mlx_ptr) DES : Both X-Window and MacOSX graphical systems are bi-directionnal. On one hand, the program sends orders to the screen to display pixels, images, and so on. On the other hand, it can get information from the keyboard and mouse associated to the screen. To do so, the program receives "events" from the keyboard or the mouse. To receive events, you must use this function. This function never returns. It is an infinite loop that waits for an event, and then calls a user-defined function associated with this event. A single parameter is needed, the connection identifier mlx_ptr. 14. mlx_key_hook & mlx_mouse_hook & mlx_expose_hook

SYM : int mix_key_hook(void *win_ptr, int (*funct_ptr)(), void *param) SYM : int mix_mouse_hook(void *win_ptr, int (*funct_ptr)(), void *param) SYM : int mix_expose_hook(void *win_ptr, int (*funct_ptr)(), void *param) DES : The three functions work exactly the same way. funct_ptr is a pointer to the function you want to be called when an event occurs. This assignment is specific to the window defined by the win_ptr identifier. The param address will be passed to the function everytime it is called, and should be used to store the parameters it might need. 17. mlx_loop_hook

SYM : int mix_loop_hook(void *win_ptr, int (*funct_ptr)(), void *param)

DES : THis function is identical to the previous ones, but the given function will be called when no event occurs. When it catches an event, the MiniLibX calls the corresponding function with fixed parameters :

expose_hook(void *param)

key_hook(int keycode,void *param)

mouse_hook(int button,int x,int y,void *param)

loop_hook(void *param)

These function names are arbitrary. They here are used to distinguish parameters according to the event. These functions are NOT part of the MiniLibX.

param is the address specified in the mlx_*_hook calls. This address is never used nor modified by the MiniLibX. On key and mouse events, additional information is passed: keycode tells you which key is pressed, (x, y) are the coordinates of the mouse click in the window, and button tells you which mouse button was pressed.
