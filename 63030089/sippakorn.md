## 63030089 สิปปกร เล่งวงศ์

ข้อที่ 1 วิ่งไปสุดปลายทางแล้ววิ่งกลับ 



https://user-images.githubusercontent.com/92081957/205985174-3f04962f-78e1-4547-87aa-ede4f2f2c1a9.mp4


```c
    #include <stdio.h>
    #include <stdbool.h>
    #include <unistd.h>
    #include "driver/gpio.h"
    uint32_t ON_time = 500000;
    uint32_t OFF_time = 0;
    uint8_t LEDIO[16] = { 23, 22, 1, 3, 21, 19, 18, 5, 18, 19, 21, 3, 1, 22, 23 };
    void app_main(void)
    {
        for (uint8_t i = 0; i < 8; i++)
        {
            gpio_reset_pin(LEDIO[i]);
        }
        for (uint8_t i = 0; i < 8; i++)
        {
            gpio_set_direction(LEDIO[i], GPIO_MODE_OUTPUT);
        }
        uint8_t ledNum = 0;
        while (true)
        {
            gpio_set_level(LEDIO[ledNum], 1);
            usleep(ON_time);
            gpio_set_level(LEDIO[ledNum], 0);
            usleep(OFF_time);
            ledNum++;
            if (ledNum == 16)
                ledNum = 0;
        }
    }
```
##
ข้อที่ 2 ยืด-หด



https://user-images.githubusercontent.com/92081957/205985279-2b82e3f6-4d82-4a60-a062-e1091baa4d5a.mp4


```c
    #include <stdio.h>
    #include <stdbool.h>
    #include <unistd.h>
    #include "driver/gpio.h"
    uint32_t ON_time = 500000;
    uint32_t OFF_time = 0;
    uint8_t LEDIO[9] = { 23, 22, 1, 3, 21, 19, 18, 5 };
    void app_main(void)
    {
        for (uint8_t i = 0; i < 8; i++)
        {
            gpio_reset_pin(LEDIO[i]);
        }
        for (uint8_t i = 0; i < 8; i++)
        {
            gpio_set_direction(LEDIO[i], GPIO_MODE_OUTPUT);
        }
        uint8_t ledNum = 0;
        while (true)
        {
            gpio_set_level(LEDIO[ledNum], 1);
            usleep(ON_time);
            ledNum++;
            if (ledNum == 9)
            {
            	for (int i = 0; i < 9; i++)
            	{
            		gpio_set_level(LEDIO[ledNum], 0);
            		usleep(ON_time);
            		ledNum--;
            	}
            }
        }
    }
```
##
ข้อที่ 3 ขยายออก


https://user-images.githubusercontent.com/92081957/205985362-f9c2ce2a-098c-4e51-afab-fbb2bcd8a7a7.mp4


```c
    #include <stdio.h>
    #include <stdbool.h>
    #include <unistd.h>
    #include "driver/gpio.h"
    uint32_t ON_time = 500000;
    uint32_t OFF_time = 0;
    uint8_t LEDIO[9] = { 23, 22, 1, 3, 21, 19, 18, 5 };
    void app_main(void)
    {
        for (uint8_t i = 0; i < 8; i++)
        {
            gpio_reset_pin(LEDIO[i]);
        }
        for (uint8_t i = 0; i < 8; i++)
        {
            gpio_set_direction(LEDIO[i], GPIO_MODE_OUTPUT);
        }
        uint8_t ledNum = 0;
        int swcase = 0;
        while (true)
        {
        	swcase++;
        	switch (swcase){
        		case 1:
        			gpio_set_level(LEDIO[3], 1);
        			gpio_set_level(LEDIO[4], 1);
        			usleep(ON_time);
        			gpio_set_level(LEDIO[3], 0);
        			gpio_set_level(LEDIO[4], 0);
        			break;
        		case 2:
        			gpio_set_level(LEDIO[2], 1);
        			gpio_set_level(LEDIO[5], 1);
        			usleep(ON_time);
        			gpio_set_level(LEDIO[2], 0);
        			gpio_set_level(LEDIO[5], 0);
        			break;
        		case 3:
        			gpio_set_level(LEDIO[1], 1);
        			gpio_set_level(LEDIO[6], 1);
        			usleep(ON_time);
        			gpio_set_level(LEDIO[1], 0);
        			gpio_set_level(LEDIO[6], 0);
        			break;
        		case 4:
        			gpio_set_level(LEDIO[0], 1);
        			gpio_set_level(LEDIO[7], 1);
        			usleep(ON_time);
        			gpio_set_level(LEDIO[0], 0);
        			gpio_set_level(LEDIO[7], 0);
        			break;
        		case 5:
        			gpio_set_level(LEDIO[1], 1);
        			gpio_set_level(LEDIO[6], 1);
        			usleep(ON_time);
        			gpio_set_level(LEDIO[1], 0);
        			gpio_set_level(LEDIO[6], 0);
        			break;
        		case 6:
        			gpio_set_level(LEDIO[2], 1);
        			gpio_set_level(LEDIO[5], 1);
        			usleep(ON_time);
        			gpio_set_level(LEDIO[2], 0);
        			gpio_set_level(LEDIO[5], 0);
        			swcase = 0;
        			break;
        	}
        }
    }
```
##
ข้อที่ 4 ยุบเข้า


https://user-images.githubusercontent.com/92081957/205985420-94904e9d-a7f0-4963-8897-54f503ff2694.mp4


```c
    #include <stdio.h>
    #include <stdbool.h>
    #include <unistd.h>
    #include "driver/gpio.h"
    uint32_t ON_time = 500000;
    uint32_t OFF_time = 0;
    uint8_t LEDIO[9] = { 23, 22, 1, 3, 21, 19, 18, 5 };
    void app_main(void)
    {
        for (uint8_t i = 0; i < 8; i++)
        {
            gpio_reset_pin(LEDIO[i]);
        }
        for (uint8_t i = 0; i < 8; i++)
        {
            gpio_set_direction(LEDIO[i], GPIO_MODE_OUTPUT);
        }
        uint8_t ledNum = 0;
        int swcase = 0;
        while (true)
        {
        	swcase++;
        	switch (swcase){
        		case 1:
        			gpio_set_level(LEDIO[0], 1);
        			gpio_set_level(LEDIO[7], 1);
        			usleep(ON_time);
        			gpio_set_level(LEDIO[0], 0);
        			gpio_set_level(LEDIO[7], 0);
        			break;
        		case 2:
        			gpio_set_level(LEDIO[1], 1);
        			gpio_set_level(LEDIO[6], 1);
        			usleep(ON_time);
        			gpio_set_level(LEDIO[1], 0);
        			gpio_set_level(LEDIO[6], 0);
        			break;
        		case 3:
        			gpio_set_level(LEDIO[2], 1);
        			gpio_set_level(LEDIO[5], 1);
        			usleep(ON_time);
        			gpio_set_level(LEDIO[2], 0);
        			gpio_set_level(LEDIO[5], 0);
        			break;
        		case 4:
        			gpio_set_level(LEDIO[3], 1);
        			gpio_set_level(LEDIO[4], 1);
        			usleep(ON_time);
        			gpio_set_level(LEDIO[3], 0);
        			gpio_set_level(LEDIO[4], 0);
        			break;
        		case 5:
        			gpio_set_level(LEDIO[2], 1);
        			gpio_set_level(LEDIO[5], 1);
        			usleep(ON_time);
        			gpio_set_level(LEDIO[2], 0);
        			gpio_set_level(LEDIO[5], 0);
        			break;
        		case 6:
        			gpio_set_level(LEDIO[1], 1);
        			gpio_set_level(LEDIO[6], 1);
        			usleep(ON_time);
        			gpio_set_level(LEDIO[1], 0);
        			gpio_set_level(LEDIO[6], 0);
        			swcase = 0;
        			break;
        	}
        }
    }
```
