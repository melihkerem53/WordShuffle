#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>
#include <time.h>
#include <stdlib.h>

#define BOYUT 100
#define BOYUT2 15

void DiziKarıstır(char* TekKelime[], int say)
{
	for (int i = 0; i < say; i++)
	{
		int j = rand() % (i + 1);

		char* temp = TekKelime[i];
		TekKelime[i] = TekKelime[j];
		TekKelime[j] = temp;
	}
}

int main() {

	char metin[BOYUT];

	printf("Metin girin:");
	fgets(metin, sizeof(metin), stdin);
	metin[strcspn(metin, "\n")] = '\0';

	char *token;
	token = strtok(metin, " ");

	int say = 0;
	char *TekKelime[BOYUT2];

	while (token != NULL)
	{
		TekKelime[say] = token;
		token = strtok(NULL, " ");
		say++;
	}

	srand(time(NULL));
	DiziKarıstır(TekKelime, say);

	for (int i = 0; i < say; i++)
	{
		printf("%s ", TekKelime[i]);
	}

	return 0;
}

