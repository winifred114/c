/*
#include <avr/io.h>
#include <avr/interrupt.h>
#include <util/delay.h>

volatile int cnt=0, a=0, sw1=0, sw2=0, mode1=0, mode2=0;

void com(unsigned char byte)
{
   _delay_ms(2);

   PORTA=byte&0xf0;
   PORTA&=0b11111100;
   _delay_us(1);
   PORTA|=0b00000100;
   _delay_us(1);
   PORTA&=0b11111011;

   PORTA=(byte<<4)&0xf0;
   PORTA&=0b11111100;
   _delay_us(1);
   PORTA|=0b00000100;
   _delay_us(1);
   PORTA&=0b11111011;
}
void data(unsigned char byte)
{
   _delay_ms(2);

   PORTA=byte&0xf0;
   PORTA|=0b00000001;
   PORTA&=0b11111101;
   _delay_us(1);
   PORTA|=0b00000100;
   _delay_us(1);
   PORTA&=0b11111011;

   PORTA=(byte<<4)&0xf0;
   PORTA|=0b00000001;
   PORTA&=0b11111101;
   _delay_us(1);
   PORTA|=0b00000100;
   _delay_us(1);
   PORTA&=0b11111011;
}
void lcd()
{
   _delay_ms(30);

   com(0b00101000);
   _delay_us(39);

   com(0b00001100);
   _delay_ms(1.53);

   com(0b00000001);
   _delay_ms(1.53);

   com(0b00000110);
}
*/
/*
// 1
void num(unsigned int a){
   unsigned char i=‘0’;
   i = '0'+a;
   data(i);
}

int main(){
   DDRA=0xff;
   EIMSK=0x03;
   EICRA=0x0f;
   TCCR0=12;
   OCR0=249;
   TIMSK=2;
   SREG=0x80;

   lcd();

   while(1){
      while(mode1==0){
         sw1=0;
         com(0x80);
         num(0);
      }
      while(mode1==1){
         sw1=0;
         com(0x80);
         num(a);
      }
      while(mode2==1){
         sw2=0;
         com(0x80);
         num(a);
      }
   }
}
ISR(TIMER0_COMP_vect){
   if(mode1==1){
      cnt++;
      if(cnt==1000)
      {
         cnt=0;
         a++;
         if(a==10) a=0;
      }
   }
}
ISR(INT0_vect){
   sw1++;
   if(sw1==1){
      mode1++;
      mode2=0;
   }
}
ISR(INT1_vect){
   sw2++;
   if(sw2==1){
      mode1=0;
      mode2++;
   }
}
*/
/*
// 2
void string(char *n)
{
   while(*n) data(*n++);
}
void umm(unsigned int a){
   if(a==0) string("do ");
   if(a==1) string("re ");
   if(a==2) string("mi ");
   if(a==3) string("fa ");
   if(a==4) string("sol");
   if(a==5) string("ra ");
   if(a==6) string("ci ");
   if(a==7) string("ddo");
}

int main(){
   DDRA=0xff;
   EIMSK=0x03;
   EICRA=0x0f;
   TCCR0=4;
   TCNT0=6;
   TIMSK=1;
   SREG=0x80;

   lcd();

   while(1){
      while(mode1==0){
         sw1=0;
         com(0x80);
         umm(a);
      }
      while(mode1==1){
         sw1=0;
         com(0x80);
         umm(a);
      }
      while(mode2==1){
         sw2=0;
         com(0x80);
         umm(a);
      }
   }
}
ISR(TIMER0_OVF_vect){
   if(mode1==1){
      TCNT0=6; cnt++;
      if(cnt==1000)
      {
         cnt=0;
         a++;
         if(a==8) a=0;
      }
   }
}
ISR(INT0_vect){
   sw1++;
   if(sw1==1){
      mode1++;
      mode2=0;
   }
}
ISR(INT1_vect){
   sw2++;
   if(sw2==1){
      mode1=0;
      mode2++;
   }
}
*/
/*
// 3
void string(char *n)
{
   while(*n) data(*n++);
}
void umm(unsigned int a){
   if(a==0) string("do ");
   if(a==1) string("re ");
   if(a==2) string("mi ");
   if(a==3) string("fa ");
   if(a==4) string("sol");
   if(a==5) string("ra ");
   if(a==6) string("ci ");
   if(a==7) string("ddo");
}

int main(){
   DDRA=0xff;
   EIMSK=0x03;
   EICRA=0x0f;
   TCCR0=12;
   OCR0=249;
   TIMSK=2;
   SREG=0x80;

   lcd();

   while(1){
      while(mode1==0){
         sw1=0;
         com(0x80);
         umm(a);
      }
      while(mode1==1){
         sw1=0;
         com(0x80);
         umm(a);
      }
      while(mode2==1){
         sw2=0;
         com(0x80);
         umm(a);
      }
   }
}
ISR(TIMER0_COMP_vect){
   if(mode1==1){
      cnt++;
      if(cnt==1000)
      {
         cnt=0;
         a++;
         if(a==8) a=0;
      }
   }
}
ISR(INT0_vect){
   sw1++;
   if(sw1==1){
      mode1++;
      mode2=0;
   }
}
ISR(INT1_vect){
   sw2++;
   if(sw2==1){
      mode1=0;
      mode2++;
   }
}
*/
/*
//4
void do6(){
   PORTB=0x10;
   _delay_us(478);
   PORTB=0x00;
   _delay_us(478);
}
void re6(){
   PORTB=0x10;
   _delay_us(426);
   PORTB=0x00;
   _delay_us(426);
}
void me6(){
   PORTB=0x10;
   _delay_us(380);
   PORTB=0x00;
   _delay_us(380);
}
void fa6(){
   PORTB=0x10;
   _delay_us(358);
   PORTB=0x00;
   _delay_us(358);
}
void sol6(){
   PORTB=0x10;
   _delay_us(319);
   PORTB=0x00;
   _delay_us(319);
}
void la6(){
   PORTB=0x10;
   _delay_us(284);
   PORTB=0x00;
   _delay_us(284);
}
void ci6(){
   PORTB=0x10;
   _delay_us(252);
   PORTB=0x00;
   _delay_us(252);
}
void do7(){
   PORTB=0x10;
   _delay_us(239);
   PORTB=0x00;
   _delay_us(239);
}
int main(){
   DDRA=0xff;
   DDRB=0xff;
   EIMSK=0x03;
   EICRA=0x0f;
   TCCR0=4;
   TCNT0=6;
   TIMSK=1;
   SREG=0x80;
   
   while(1){
      while(mode1==0){
         sw1=0;
         do6();
      }
      while(mode1==1){
         sw1=0;
         if(a==0) do6();
         if(a==1) re6();
         if(a==2) me6();
         if(a==3) fa6();
         if(a==4) sol6();
         if(a==5) la6();
         if(a==6) ci6();
         if(a==7) do7();
      }
      while(mode2==1){
         sw2=0;
      }
   }   
}
ISR(TIMER0_OVF_vect){
   if(mode1==1){
      TCNT0=6; cnt++;
      if(cnt==1000)
      {
         cnt=0;
         a++;
         if(a==8) a=0;
      }
   }
}
ISR(INT0_vect){
   sw1++;
   if(sw1==1){
      mode1++;
      mode2=0;
   }
}
ISR(INT1_vect){
   sw2++;
   if(sw2==1){
      mode1=0;
      mode2++;
   }
}
*/
/*
//5
void do6(){
   PORTB=0x10;
   _delay_us(478);
   PORTB=0x00;
   _delay_us(478);
}
void re6(){
   PORTB=0x10;
   _delay_us(426);
   PORTB=0x00;
   _delay_us(426);
}
void me6(){
   PORTB=0x10;
   _delay_us(380);
   PORTB=0x00;
   _delay_us(380);
}
void fa6(){
   PORTB=0x10;
   _delay_us(358);
   PORTB=0x00;
   _delay_us(358);
}
void sol6(){
   PORTB=0x10;
   _delay_us(319);
   PORTB=0x00;
   _delay_us(319);
}
void la6(){
   PORTB=0x10;
   _delay_us(284);
   PORTB=0x00;
   _delay_us(284);
}
void ci6(){
   PORTB=0x10;
   _delay_us(252);
   PORTB=0x00;
   _delay_us(252);
}
void do7(){
   PORTB=0x10;
   _delay_us(239);
   PORTB=0x00;
   _delay_us(239);
}
void string(char *n)
{
   while(*n) data(*n++);
}
int main(){
   DDRA=0xff;
   DDRB=0xff;
   EIMSK=0x03;
   EICRA=0x0f;
   TCCR0=4;
   TCNT0=6;
   TIMSK=1;
   SREG=0x80;

   lcd();
   com(0x80);
   string("do ");
   while(1){
      while(mode1==0){
         sw1=0;
         do6();
      }
      while(mode1==1){
         sw1=0;
         if(a==0) do6();
         if(a==1) re6();
         if(a==2) me6();
         if(a==3) fa6();
         if(a==4) sol6();
         if(a==5) la6();
         if(a==6) ci6();
         if(a==7) do7();
      }
      while(mode2==1){
         sw2=0;
      }
   }   
}
ISR(TIMER0_OVF_vect){
   if(mode1==1){
      TCNT0=6; cnt++;
      if(cnt==1000)
      {
         cnt=0;
         a++;
         com(0x80);
         if(a==1) string("re ");
         if(a==2) string("mi ");
         if(a==3) string("fa ");
         if(a==4) string("sol");
         if(a==5) string("ra ");
         if(a==6) string("ci ");
         if(a==7) string("ddo");
         if(a==8) a=0;
         if(a==0) string("do ");
      }
   }
}
ISR(INT0_vect){
   sw1++;
   if(sw1==1){
      mode1++;
      mode2=0;
   }
}
ISR(INT1_vect){
   sw2++;
   if(sw2==1){
      mode1=0;
      mode2++;
   }
}
*/
/*
// 6
void timer(unsigned int a, unsigned int b, unsigned int c)
{
   unsigned char w[]="00000000";
   int j=0;
   w[0]='0'+(c%100)/10;
   w[1]='0'+(c%10);
   w[2]=':';
   w[3]='0'+(b%100)/10;
   w[4]='0'+(b%10);
   w[5]=':';
   w[6]='0'+(a%100)/10;
   w[7]='0'+(a%10);
   
   for(j=0;j<8;j++)
   {
      data(w[j]);
   }
}
void string(char *n)
{
   while(*n) data(*n++);
}

volatile int a=0, b=0, c=0, cnt=0;
int main()
{
   DDRA=0xff;
   TCCR0=4;
   TCNT0=6;
   TIMSK=1;
   SREG=0x80;

   lcd();

   while(1)
   {
      com(0x86);
      string("TIME");
      com(0xc4);

      timer(a,b,c);
   }
}
ISR(TIMER0_OVF_vect)
{
   TCNT0=6; cnt++;
   if(cnt==1000)
   {
      a++;
      if(a>59) { a=0; b++; }
      if(b>59) { a=0; b=0; c++; }
      if(c>23) { a=0; b=0; c=0; }
      cnt=0;
   }
}
*/
#define F_CPU 16000000UL
#include <avr/io.h>
#include <avr/interrupt.h>
#include <util/delay.h>
#define  ECHO 7  //8번 문제
#define  TRIG 6  //8번 문제
#define  VELO 340UL  //8번 문제

void COMMAND(unsigned char byte)   // 명령어 함수
{
   _delay_ms(2);

   PORTA = byte&0xf0;      // 명령어 쓰기
   PORTA &= 0b11111100;      // RS = 0, RW = 0, 명령어를 쓰도록 설정
   _delay_us(1);                 // RS & RW setup time 40ns 지연
   PORTA |= 0b00000100;      // E = 1, lcd 동작
   _delay_us(1);                // E pulse width time 230ns 지연
   PORTA &= 0b11111011;      // E = 0

   PORTA = (byte<<4)&0xf0;   // 명령어 쓰기
   PORTA &= 0b11111100;      // RS = 0, RW = 0, 명령어를 쓰도록 설정
   _delay_us(1);                 // RS & RW setup time 40ns 지연
   PORTA |= 0b00000100;      // E = 1, lcd 동작
   _delay_us(1);                // E pulse width time 230ns 지연
   PORTA &= 0b11111011;      // E = 0
}

void LCD_INIT(void)         // 초기설정 함수
{
   _delay_ms(30);      // 전원 투입 후 30ms 이상 지연
   
   //Function set
   COMMAND(0b00101000);   // 인터페이스(DL)=0(4bit), 라인(N)=1(2라인), 폰트(F)=0(5*7 dot)   _delay_us(39);      // 39us 이상 지연

   //Display ON/OFF Control
   COMMAND(0b00001100);   // 화면 표시(D)=1(on), 커서(C)=1(on), 네모(B)=1(on 깜빡임)   _delay_us(39);      // 39us 이상 지연

   //Display Clear
   COMMAND(0b00000001);   // 화면을 클리어하고 , 커서가 홈위치인 0번지로 돌아감.
   _delay_ms(1.53);      // 1.53ms 이상 지연

   //Entry Mode Set
   COMMAND(0b00000110);   // 커서방향(I/D)=1(address증가), 표시이동(S)=0(이동하지 않음)
}

void DATA(unsigned char byte)      // 데이터 함수
{
   _delay_ms(2);

   PORTA = byte&0xf0;      // 데이터 쓰기
   PORTA |= 0b00000001;      // RS = 1, 데이터를 쓰도록 설정
   PORTA &= 0b11111101;      // RW = 0, 데이터를 쓰도록 설정
   _delay_us(1);                 // RS & RW setup time 40ns 지연
   PORTA |= 0b00000100;      // E = 1, lcd 동작
   _delay_us(1);                // E pulse width time 230ns 지연
   PORTA &= 0b11111011;      // E = 0

   PORTA = (byte<<4)&0xf0;   // 데이터 쓰기
   PORTA |= 0b00000001;      // RS = 1, 데이터를 쓰도록 설정
   PORTA &= 0b11111101;      // RW = 0, 데이터를 쓰도록 설정
   _delay_us(1);                 // RS & RW setup time 40ns 지연
   PORTA |= 0b00000100;      // E = 1, lcd 동작
   _delay_us(1);                // E pulse width time 230ns 지연
   PORTA &= 0b11111011;      // E = 0
}

/*
int main(void)   //1번
{
   DDRA = 0xff;


   LCD_INIT();

   COMMAND(0xc6);

   while(1){
      _delay_ms(500);
      COMMAND(0b00001110);
      _delay_ms(500);
      COMMAND(0b00001100);
   }
}
*/

/*
volatile int cnt=0;  //문제2번 .OVF

ISR(TIMER0_OVF_vect){
   cnt++;
   if(cnt==500){TCNT0=6;
      COMMAND(0b00001110);
   } //0.5s
   if(cnt==1000){TCNT0=6; cnt=0;
   COMMAND(0b00001100);}
}

int main(void)   
{
   DDRA = 0xff;
   PORTA = 0x00;
   
   LCD_INIT();
   
   COMMAND(0x86);
   
   TCCR0=0x04; TCNT0=6; TIMSK=0x01;  //TCCR0 4= 64, 5=128, 6=256/ TCCR2 3=64, (4=128), 5=256, 6=512, 7=1024
   SREG=0x80;
   
   while(1);
}
*/

/*
volatile int cnt=0;  //2번 출력비교

ISR(TIMER0_COMP_vect)
{
   cnt++;
   if(cnt==500) COMMAND(0x0e); //0b00001110; display 커서on
   if(cnt==1000) {COMMAND(0x0c); cnt=0;} //0b00001100 커서off
}

int main(void)
{
   DDRA=0xff;
   PORTA=0x00;
   
   SREG|=0x80;
   TCCR0=0x0c; //64분주
   OCR0=249; 
   TIMSK=2;
   
   LCD_INIT();
   
   COMMAND(0xc4);
   
   while(1);
}
*/

/*
void STRING(unsigned char font[],unsigned char a) //문제 3번
{
   unsigned char i;
   for(i=0;i<a;i++){
      DATA(font[i]);
   }
}

int main(){
   
   unsigned char string_1[]="Y";
   unsigned char string_2[]="S";
   unsigned char string_3[]="J";

   DDRA=0xff;
   PORTA=0x00;
   
   LCD_INIT();

   COMMAND(0x86);
   STRING(string_1,1);
   _delay_ms(500);
   COMMAND(0x87);
   STRING(string_2,1);
   _delay_ms(500);
   COMMAND(0x88);
   STRING(string_3,1);
   _delay_ms(500);

   while(1);
}
*/

/*
//4번 오버플로우
volatile int cnt=0;
int main(void)
{
   DDRA=0xff;
   SREG|=0x80;
   TCCR1B=4;
   TCNT1=34286;
   TIMSK=4;
   
   LCD_INIT();
   
   while(1);
   
}
ISR(TIMER1_OVF_vect)
{
   TCNT1=34286; cnt++;
   if(cnt==1)
   {
      COMMAND(0xc6);
      DATA('K');
   }
   if(cnt==2)
   {
      _delay_ms(500);
      COMMAND(0xc5);
      DATA('C');
   }
   if(cnt==3)
   {
      _delay_ms(500);
      COMMAND(0xc4);
      DATA('E');
      COMMAND(0xc3); //마지막 커서 위치
   }
}
*/

/*
//4번 비교매치
volatile int cnt=0;
int main(void)
{
   DDRA=0xff;
   SREG|=0x80;
   TCCR1A=0;
   TCCR1B=0x0c; //256분주, 500sec 간격
   OCR1A=31249;
   TIMSK=0x10;
   
   LCD_INIT();
   
   while(1);
   
}
ISR(TIMER1_COMPA_vect)
{
   cnt++;
   if(cnt==1)
   {
      COMMAND(0xc4);
      DATA('K');
   }
   if(cnt==2)
   {
      _delay_ms(500);
      //COMMAND(0xc5);
      DATA('C');
   }
   if(cnt==3)
   {
      _delay_ms(500);
      //COMMAND(0xc6);
      DATA('E');
   }
}
*/

/*
void STRING(unsigned char font[],unsigned char a)     //문제 5번    //Display ON/OFF Control COMMAND(0b00001110); 맨 마지막 0으로
{
   unsigned char i;
   for(i=0;i<a;i++){
      DATA(font[i]);
   }
}

int main(){
   
   unsigned char string_1[]="TIME";
   unsigned char string_2[]="00:00:00";

   DDRA=0xff;
   PORTA=0x00;
   
   LCD_INIT();

   COMMAND(0x86);
   STRING(string_1,4);
   COMMAND(0xc4);
   STRING(string_2,8);

//   BLINK(5000);
   while(1);
}
*/

/*
void STRING(unsigned char font[],unsigned char a)     //6번   
{
   unsigned char i;
   for(i=0;i<a;i++){
      DATA(font[i]);
   }
}
volatile int start=1, sw1=0, mode1=0;
int main(void)
{
   unsigned char a1[]="TIME";
   unsigned char a2[]="00:00:00";
   DDRA=0xff;
   DDRE=0x00;
   
   SREG|=0x80;
   EIMSK=0xff;
   EICRA=0xff;
   
   LCD_INIT();
   
   while(1)
   {
      while(start)
      {
         COMMAND(0x86);
         STRING(a1,4);
         COMMAND(0xc4);
         STRING(a2,8);
         if(sw1)start=0;
      }
      while(mode1==1)
      {
         sw1=0;
         _delay_ms(500);
         COMMAND(0x08); //display on
         _delay_ms(500);
         COMMAND(0x0C);  //display off
      }
      while(mode1==2)
      {
         sw1=0, mode1=0, start=1;
      }
   }
}
ISR(INT0_vect)
{
   sw1++;
   if(sw1==1) mode1++; _delay_ms(10);
}
*/

/*
void STRING(unsigned char font[],unsigned char a)     //7번
{
   unsigned char i;
   for(i=0;i<a;i++){
      DATA(font[i]);
   }
}

volatile int i=0;
volatile int start=1, sw1=0,sw2=0, mode1=0, mode2=0;
int main(void)
{
   unsigned char a1[]="TIME";
   unsigned char a2[]="00:00:00";
   DDRA=0xff;
   DDRD=0x00;
   
   SREG|=0x80;
   EIMSK=0xff;
   EICRA=0xff;
   
   LCD_INIT();
   
   while(1)
   {
      while(mode1==0)  //초기상태
      {
         COMMAND(0x86);
         STRING(a1,4);
         COMMAND(0xc4);
         STRING(a2,8);
      }
      
      while(mode1==1)
      {
         sw1=0;
         for(i=0; i<2; i++)
         {
            if(mode1==1)
            {
               _delay_ms(500);
               COMMAND(0x18); //18 왼쪽으로 두칸이동
            }
         }
         for(i=0; i<4; i++)
         {
            if(mode1==1)
            {
               _delay_ms(500);
               COMMAND(0x1C); //1c 오른쪽으로 두칸이동
            }
         }
         for(i=0; i<2; i++)
         {
            if(mode1==1)
            {
               _delay_ms(500);
               COMMAND(0x18);
            }
         }
      }
      while(mode1==2)
      {
         sw1=0;
      }
      if(mode2==1)
      {
         LCD_INIT();
         sw2=0;
      }
   }
}
ISR(INT0_vect)
{
   sw1++;
   if(sw1==1)
   {
      mode1++;
      if(mode1>2) mode1=1;
      _delay_ms(10);
   }
}
ISR(INT1_vect)
{
   mode1=0;
   sw2=1;
}
*/

/*
void STRING(unsigned char font[],unsigned char a) //문제 8번
{
   unsigned char i;
   for(i=0;i<a;i++){
      DATA(font[i]);
   }
}

void STRING_n(unsigned int Num)
{
   unsigned char a[]="00000";
   int i=0;
   
   a[0]='0'+(Num%10000)/1000;
   a[1]='0'+(Num%1000)/100;
   
   a[2]='.';
   a[3]='0'+(Num%100)/100;
   a[4]='0'+(Num%10);
   
   for(i=0; i<5; i++)
   {
      DATA(a[i]);
   }
}
int main()
{
   unsigned int d;
   unsigned char a1[]="dis=";
   unsigned char a2[]="SPEED:";
   
   DDRA=0xff;
   DDRB=0xff;
   DDRF=((DDRF|(1<<TRIG))&~(1<<ECHO));
   TCCR0=0x6b;
   LCD_INIT();
   
   while(1)
   {
      TCCR1B=0x03;    //책에 코드 그대로 있음
      PORTF &= ~(1<<TRIG);
      _delay_us(10);
      PORTF |= (1<<TRIG);
      _delay_us(10);
      PORTF &= ~(1<<TRIG);
      while(!(PINF&(1<<ECHO)));
      
      TCNT1=0x00;
      while(PINF & (1<<ECHO));
      
      TCCR1B=0x00;
      d = (unsigned int)(VELO*(TCNT1*4/2)/100);  // define echo 7, trig 6, velo(속도)340ul  //여기 까지 283 페이지 쯤 
      
      COMMAND(0x83);
      STRING(a1,4);
      STRING_n(d);
      
      COMMAND(0xc3);
      STRING(a2,6);
      
      if(d>=2000) {DATA('1'); OCR0=50;}
      else if(d<2000&&d>=500) {DATA('2'); OCR0=120;}
      else if(d<500) {DATA('3'); OCR0=255;}
   }
}
*/
