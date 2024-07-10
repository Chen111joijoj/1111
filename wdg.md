/*
 * wdg.h
 *
 * created: 2024/6/28
 *  author: 
 */

#ifndef _WDG_H
#define _WDG_H

#ifdef __cplusplus
void WdgInit(void);
void WDG_SetWatchDog(uint32_t time);
void WDG_DogFeed(void);
void my_delay(volatile int i);
extern "C" {
#endif



#ifdef __cplusplus
}
#endif

#endif // _WDG_H

