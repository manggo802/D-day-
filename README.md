# D-day
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>                                
#include <time.h>

#define DAYSEC (24*60*60)

int main(void) {
    int year = 0;
    int mon = 0;
    int day = 0;

    printf("========D-day 프로그램============\n");
    printf("원하는 년도를 입력해주세요(단 숫자만 적을것)\n");
    scanf_s("%d", &year);

    printf("원하는 달를 입력해주세요(단 숫자만 적을것)\n");
    scanf_s("%d", &mon);

    printf("원하는 날짜를 입력해주세요(단 숫자만 적을것)\n");
    scanf_s("%d", &day);
    

    time_t now;
    struct tm tm_now, tm_dday = { 0,0,0,day,mon,year };
    int now_sec, dday_sec, left_days;

    now = time(NULL);
    tm_now = *localtime(&now);

    tm_dday.tm_year -= 1900;
    tm_dday.tm_mon -= 1;

    tm_now.tm_hour = 0;
    tm_now.tm_min = 0;
    tm_now.tm_sec = 0;

    now_sec = mktime(&tm_now);
    dday_sec = mktime(&tm_dday);

    left_days = (dday_sec - now_sec) / DAYSEC;

    printf("오늘의 날짜는 %s", ctime(&now));
    printf("오늘부터 %d년 %d월 %d일까지는 %d일 남았습니다. \n",
        tm_dday.tm_year + 1900, tm_dday.tm_mon + 1, tm_dday.tm_mday, left_days );


    return 0;
}
struct 과 tm함수를 이용한 D-day함수를 만들어 보았습니다!
