%{
#include <stdio.h>
#include <stdlib.h>
%}

%%
[01]+  {
        int decimal = 0;
        char *binary = yytext;

        // Convert binary string to decimal
        for (int i = 0; binary[i] != '\0'; i++) {
            decimal = decimal * 2 + (binary[i] - '0');
        }

        printf("Binary: %s -> Decimal: %d\n", binary, decimal);
    }

.|\n    ; // Ignore any other character

%%

int main(int argc, char **argv)
{
    printf("Enter binary numbers (Ctrl+D to end):\n");
    yylex();
    return 0;
}

int yywrap()
{
    return 1;
}
