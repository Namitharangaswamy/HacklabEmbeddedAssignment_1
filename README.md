
#include <stdio.h>
#include <stdbool.h>
#include <time.h>

typedef enum {
  GREEN,
  YELLOW,
  RED
} state_t;

int main(void) {
  state_t state = GREEN;
  time_t start_time = time(NULL);
  
  while (true) {
    time_t current_time = time(NULL);
    int elapsed_time = current_time - start_time;
    
    switch (state) {
      case GREEN:
        if (elapsed_time >= 360) {
          printf("Transitioning from GREEN to YELLOW\n");
          state = YELLOW;
          start_time = current_time;
        }
        break;
        
      case YELLOW:
        if (elapsed_time >= 10) {
          printf("Transitioning from YELLOW to RED\n");
          state = RED;
          start_time = current_time;
        }
        break;
        
      case RED:
        if (elapsed_time >= 120) {
          printf("Transitioning from RED to GREEN\n");
          state = GREEN;
          start_time = current_time;
        }
        break;
    }
    
    switch (state) {
      case GREEN:
        printf("GREEN light is ON\n");
        break;
        
      case YELLOW:
        printf("YELLOW light is ON\n");
        break;
        
      case RED:
        printf("RED light is ON\n");
        break;
    }
  }
  
  return 0;
}
