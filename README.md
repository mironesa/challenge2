# challenge2
// Created on Mon March 23 2020
int l_motor = 0 ;
int r_motor = 2 ;
int speed = 50 ; 
int speed2 = 25 ;
int pause = 450 ;
int target = 300 ;
int right_side = 2 ;
int front = 1 ;
int wall = 300 ;

void forward(){
   motor(l_motor,speed); //go forward 
   motor(r_motor,speed);
}
void r_turn(){
   motor(l_motor,speed); //right turn
   motor(r_motor,-speed);
}
void right_veer() {
	motor(l_motor,speed); //veer right
   motor(r_motor,speed2);
}
void left_turn() {
   motor(l_motor,-speed); //turn left
   motor(r_motor,speed);
}
void left_veer() {
   motor(l_motor,speed2); //veer left
   motor(r_motor,speed);
}

int main()
{
	right_turn() ;
	msleep(pause) ;
	ao() ;
	
while(analog(front)>wall) {
	while(analog(right_side)>wall) {
	right_veer() ;	
	}
	while(analog(right_side)<wall) {
	left_veer() ;
	}
}

	left_turn();
	msleep(pause) ;
	ao() ;
	
	return 0;
}
