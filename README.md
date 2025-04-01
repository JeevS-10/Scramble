using System;
using System.ComponentModel.Design;
using System.Linq;

class Program
{
    static void Main()
    {
        string[] words = { "computer", "elephant", "guitar", "keyboard", "monitor", "software", "library", "pencil", "notebook", "telephone", "headphones", "backpack", "calculator", "television", "refrigerator", "trousers", "vehicle", "outrageous", "triangle", "astronaut", "cricket", "portugese", "scramble", "ocean", "decathlon", "dyslexia" };
        int[] wordPoints = { 10, 15, 8, 12, 10, 20, 18, 5, 7, 14, 9, 6, 11, 16, 22, 60, 13, 20, 3, 19, 6, 1, 23, 21, 27, 36 }; // Assign different points to words
        Random random = new Random();
        int points = 0;

        while (true)
        {

            int index = random.Next(words.Length - 1);
            string word = words[index];
            int wordPointValue = wordPoints[index];

            char[] scrambledArray = word.ToCharArray();
            scrambledArray = scrambledArray.OrderBy(x => random.Next()).ToArray();
            string scrambledWord = new string(scrambledArray);

            Console.WriteLine("===== Word Scramble Game =====");
            Console.WriteLine("The scrambled word is: " + scrambledWord);
            Console.Write("Your guess: ");
            string userGuess = Console.ReadLine().ToLower();

            if (userGuess == word)
            {
                Console.WriteLine("Correct! You earned " + wordPointValue + " points");
                points += wordPointValue;
            }
            else
            {
             Console.WriteLine("Incorrect! The correct word was: " + word);
            }

            Console.WriteLine("Your current points: " + points);
            Console.Write("Do you want to play again? (yes/no): ");
            string response = Console.ReadLine().ToLower();
            if (response != "yes")
            {
                
                Console.WriteLine("Thanks for playing! Your final score: " + points);
                if (points < 50)
                {
                    Console.WriteLine("Better luck next time?");
                }
                else if (points > 50)
                {
                    Console.WriteLine("Well done!");

                }
                break;
            }
        }
    }
}
