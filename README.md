# DSA  Assignment 1
#include <stdio.h>
int main()
{
    printf("Enter size of array and rotation key respectively\n");
    int z, k;
    scanf("%d %d", &z, &k);

    int arr[z];
    printf("Enter elements of array\n");
    for (int i = 0; i < z; i++)
    {
        scanf("%d", &arr[i]);
    }

    k = k % z;   
    int a = z - k;

    int rot_arr[z];

    for (int i = 0; i < z; i++)
    {
        rot_arr[i] = arr[(a + i) % z];    
    }

    int length = 1;
    int prevlength = 1;    

    for (int i = 0; i < z - 1; i++)
    {
        if (rot_arr[i] < rot_arr[i + 1])
        {
            length++;
        }
        else
        {
            if (length > prevlength)    
                prevlength = length;
            length = 1;
        }
    }

    if (length > prevlength)    
        prevlength = length;

    printf("%d", prevlength);  

    return 0;
}
