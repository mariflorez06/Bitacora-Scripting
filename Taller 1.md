namespace Taller_1
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //EjerMatriz();
            //EjerCadena();
            //EjerCiclo();
            //EjerFuncion1();
            EjerFuncion2();
        }

        static void EjerMatriz()
        {
            Console.WriteLine(" - Ejercicio: Lea una matriz nxn de chars e imprima la matriz leída y la matriz con las filas cambiadas");

            Console.WriteLine("Ingresa el tamaño de la matriz cuadrada");
            int n = int.Parse(Console.ReadLine());
            char[,] matriz = new char[n, n];

            Console.WriteLine("\n Ingresa los caracteres de la matriz");
            for (int i = 0; i < n; i++)
            {
                for (int j = 0; j < n; j++)
                {
                    Console.WriteLine($"Elemento [{i},{j}]: ");
                    matriz[i, j] = Console.ReadLine()[0];

                }
            }

            Console.WriteLine("\n Matriz Original");
            for (int i = 0; i < n; i++)
            {
                for (int j = 0; j < n; j++)
                {
                    Console.Write(matriz[i, j] + " ");
                }
                Console.WriteLine();
            }

            char[,] matrizInv = new char[n, n];
            for (int i = 0;i<n ; i++)
            {
                for (int j = 0; j < n; j++)
                {
                    matrizInv[n - 1 - i, j] = matriz[i, j];
                }
            }

            Console.WriteLine("\n Matriz Modificada");
            for (int i = 0; i < n; i++)
            {
                for (int j = 0; j < n; j++)
                {
                    Console.Write(matrizInv[i, j] + " ");
                }
                Console.WriteLine();
            }
        }

        static void EjerCadena()
        {
            Console.WriteLine(" - Ejercicio: Lea una frase de mínimo 3 palabras y convierta cada palabra a minúscula y con mayúscula inicial");

            Console.WriteLine("Ingresa una frase de MIN 3 PALABRAS");
            string frase = Console.ReadLine();


            string[] palabras = frase.Split(' ');
            int contadorPalabras = 0;

            foreach(string p in palabras)
            {
                if (p != "")
                {
                    contadorPalabras++;
                }
            }

            if (contadorPalabras < 3)
            {
                Console.WriteLine("La frase debe tener al menos 3 palabras");
                return;
            }

            string fraseFinal = "";

            foreach (string s in palabras)
            {
                if (s != "")
                {
                    char primerLetra = char.ToUpper(s[0]);
                    string restoPalabra = s.Substring(1).ToLower();
                    fraseFinal += primerLetra + restoPalabra+" ";
                }
            }

            Console.WriteLine("\n Resultado final: "+fraseFinal);

        }

        static void EjerCiclo()
        {
            Console.WriteLine(" - Ejercicio: Usando un ciclo for, calcule el factorial de un número n, tenga en cuenta validar los casos especiales");

            Console.WriteLine("Ingresa un numero para calcular su factorial");
            int n = Convert.ToInt32(Console.ReadLine());

            if (n < 0)
            {
                Console.WriteLine("El factorial no esta definido para numeros negativos");
                return;
            }
            if (n == 0 || n == 1)
            {
                Console.WriteLine($"El factorial de {n} es: 1");
                return;
            }

            long factorial = 1;
            for (int i = 1; i < n; i++)
            {
                factorial = factorial * i;
            }

            Console.WriteLine($"\n El factorial de {n} ({n}!) es: {factorial}");

        }

        static void EjerFuncion1()
        {
            Console.WriteLine(" - Ejercicio: Realice una función que lea una matriz de números enteros de NxM y calcule el promedio de cada fila y cada columna");

            Console.WriteLine("Ingrese el numero de filas (N)");
            int N = Convert.ToInt32(Console.ReadLine());
            Console.WriteLine("Ingrese el numero de columnas (M)");
            int M = Convert.ToInt32(Console.ReadLine());

            if (N <=0 || M <=0)
            {
                Console.WriteLine("Las dimensiones deben ser numeros mayores a 0");
                return;
            }

            int[,] matriz = new int[N, M];

            Console.WriteLine("Vamos a llenar la matriz");
            for (int i = 0; i < N; i++)
            {
                for (int j = 0; j < M; j++)
                {
                    Console.WriteLine($"Ingrese la posicion [{i},{j}]: ");
                    matriz[i, j] = Convert.ToInt32(Console.ReadLine());
                }
            }

            Console.WriteLine("\n Matriz Ingresada");
            for (int i = 0;i < N; i++)
            {
                for(int j = 0;j < M; j++)
                {
                    Console.Write(matriz[i, j] + "\t");
                }
                Console.WriteLine();
            }

            Console.WriteLine("\n Promedio de cada Fila");
            for (int i = 0;i<N ; i++)
            {
                int sumaFila = 0;
                for (int j = 0;j<M; j++)
                {
                    sumaFila += matriz[i, j];
                }
                double promedioFila = (double) sumaFila/M;
                Console.WriteLine($"Fila {i}: {promedioFila:F2}");
            }

            Console.WriteLine("\n Promedio de cada Columna");
            for (int j = 0; j < M; j++)
            {
                int sumaColumna = 0;
                for (int i = 0; i < N; i++)
                {
                    sumaColumna += matriz[i, j];
                }
                double promedioColumna = (double)sumaColumna / N;
                Console.WriteLine($"Columna {j}: {promedioColumna}");
            }
        }

        static void EjerFuncion2()
        {
            Console.WriteLine(" - Ejercicio: Realice una función, que lea un número de máximo 8 cifras y luego sume cada dígito hasta obtener un valor de un solo dígito");

            Console.Write("Ingresa un numero entero positivo (Max 8 cifras): ");
            string entrada = Console.ReadLine();

            if ( entrada.Length > 8)
            {
                Console.WriteLine("El numero no puede tener mas de 8 cifras");
                return;
            }

            long num;

            if (!long.TryParse( entrada, out num) || num <0)
            {
                Console.WriteLine("Debes ingresar un numero entero positico valido");
                return;
            }

            Console.WriteLine($"\n Numero Ingresado: {num}");

            while ( num >= 10)
            {
                long suma = 0;
                long temp = num;

                while ( temp > 0 )
                {
                    long ultimoDig = temp % 10;
                    suma += ultimoDig;
                    temp = temp / 10;
                }

                Console.WriteLine($"Suma intermedia: {suma}");
                num = suma;
            }

            Console.WriteLine($"\n El resultado de un solo digito es: {num}");
        }
    }
}
'''

