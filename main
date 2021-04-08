using System;
using System.IO;

namespace DynamicPrograming
{
    class Program
    {
        static int getValueFunction(int x, int y)
        {
            return (5 * x + x * y + 6 * y);
        }

        static void Main(string[] args)
        {
            int[,] cost;
            char[,] direction;
            int N;

            Console.Write("Input the size of square: ");
            N = Convert.ToInt32(Console.ReadLine());

            cost = new int[N, N];
            direction = new char[N, N];

            for (int x = (N - 1); x >= 0; x--)
            {
                for (int y = (N - 1); y >= 0; y--)
                {
                    int costX, costY; // costX for F(x+1,y), costY for F(x,y+1)

                    cost[x, y] = getValueFunction(x, y);

                    if (x == (N - 1) && y == (N - 1))
                    {
                        direction[x, y] = 'E';
                        continue;
                    }

                    if ((x + 1) <= (N - 1)) costX = cost[x + 1, y];
                    else
                    {
                        direction[x, y] = 'U';
                        cost[x, y] = cost[x, y] + cost[x, y + 1];
                        continue;
                    }

                    if ((y + 1) <= (N - 1)) costY = cost[x, y + 1];
                    else
                    {
                        direction[x, y] = 'R';
                        cost[x, y] = cost[x, y] + cost[x + 1, y];
                        continue;
                    }

                    if (costX > costY)
                    {
                        direction[x, y] = 'U';
                        cost[x, y] = cost[x, y] + cost[x, y + 1];
                    }
                    else
                    {
                        direction[x, y] = 'R';
                        cost[x, y] = cost[x, y] + cost[x + 1, y];
                    }

                }
            }

            for (int y = (N - 1); y >= 0; y--)
            {
                for (int x = 0; x < N; x++)
                {
                    Console.Write(direction[x, y] + " ");
                }
                Console.WriteLine();
            }

            for (int y = (N - 1); y >= 0; y--) 
            {
                for (int x = 0; x < N; x++) 
                {
                    Console.Write(cost[x, y] + " ");
                }
                Console.WriteLine();
            }

            int i = 0, j = 0;

            Console.Write("Path: ");

            while (direction[i,j] != 'E')
            {
                if (direction[i, j] == 'R')
                {
                    Console.Write("R ");
                    i++;
                }
                else
                {
                    Console.Write("U ");
                    j++;
                }
            }

            Console.Write("E");

            Console.ReadKey();
        }
    }
}
