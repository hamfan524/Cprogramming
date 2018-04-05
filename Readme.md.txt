#include <stdio.h>
#define MAX 5

int a[MAX] = { 4, 4, 3, 2, 1 };  
int b[MAX] = { 0, };  
int c[MAX] = { 0, };      
int *z[3] = { a, b, c };

void show() {

	int i;

	for (i = 4; i > 0; i--) 
		printf("  |%d| |%d| |%d| \n", a[i], b[i], c[i]);

	printf("--------------------\n %3c %3c %3c \n\n", 65, 66, 67);

}

void move(int from, char tmp, char to) {

	int s = tmp - 65;
	int d = to - 65;
	int x = z[s][z[s][0]];

	z[s][z[s][0]--] = 0;
	z[d][++(z[d][0])] = x;

	show();

}

void hanoi(int n, char from, char tmp, char to) {

	if (n == 1) {
		move(1, from, to);
		printf("Move disc 1 from %c to %c.\n\n", from, to);
	}

	else {

		hanoi(n - 1, from, to, tmp);

		move(n, from, to);

		printf("Move disc %d from %c to %c.\n\n", n, from, to);

		hanoi(n - 1, tmp, from, to);

	}

}


int main() {
	
	show();
	printf("The first Hanoi Top\n\n");	
	hanoi(4, 65, 66, 67);

	return 0;

}
