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

    k = k % z;   // ✅ fix: handle large k
    int a = z - k;

    int rot_arr[z];

    for (int i = 0; i < z; i++)
    {
        rot_arr[i] = arr[(a + i) % z];   // ✅ fix: removed confusing if-else
    }

    int length = 1;
    int prevlength = 1;   // ✅ fix: initialize properly

    for (int i = 0; i < z - 1; i++)
    {
        if (rot_arr[i] < rot_arr[i + 1])
        {
            length++;
        }
        else
        {
            if (length > prevlength)   // ✅ fix: track max properly
                prevlength = length;
            length = 1;
        }
    }

    if (length > prevlength)   // ✅ fix: final check
        prevlength = length;

    printf("%d", prevlength);   // ✅ fix: single clean output

    return 0;
}
