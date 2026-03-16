 #include <stdio.h>
#include <stdlib.h>
#include <time.h>

void merge(int a[], int left, int mid, int right)
{
    int i = left;
    int j = mid + 1;
    int k = left;

    int temp[100];

    while(i <= mid && j <= right)
    {
        if(a[i] < a[j])
        {
            temp[k] = a[i];
            i++;
        }
        else
        {
            temp[k] = a[j];
            j++;
        }
        k++;
    }

    while(i <= mid)
    {
        temp[k] = a[i];
        i++;
        k++;
    }

    while(j <= right)
    {
        temp[k] = a[j];
        j++;
        k++;
    }

    for(i = left; i <= right; i++)
    {
        a[i] = temp[i];
    }
}

void mergeSort(int a[], int left, int right)
{
    int mid;

    if(left < right)
    {
        mid = (left + right) / 2;

        mergeSort(a, left, mid);
        mergeSort(a, mid + 1, right);

        merge(a, left, mid, right);
    }
}

int main()
{
    int a[10];
    int i;

    srand(time(NULL));

    printf("Random array:\n");

    for(i = 0; i < 10; i++)
    {
        a[i] = rand() % 100;
        printf("%d ", a[i]);
    }

    mergeSort(a, 0, 9);

    printf("\nSorted array:\n");

    for(i = 0; i < 10; i++)
    {
        printf("%d ", a[i]);
    }

    return 0;
}
