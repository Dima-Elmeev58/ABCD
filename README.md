# ABCD
public class Program
{
    public static void Main(string[] args)
    {
        string filePath = "C:\\Users\\revno\\OneDrive\\Рабочий стол\\2 курс\\Sist_pr_21.txt";

        try
        {
            string text = File.ReadAllText(filePath);
            int maxPairs = GetMaxPairs(text);
            Console.WriteLine($"ABCD подряд = {maxPairs}");
        }
        catch (Exception e)
        {
            Console.WriteLine($"Ошибка: {e.Message}");
        }
    }

    public static int GetMaxPairs(string text)
    {
        int maxPairs = 0;
        int currentPairs = 0;

        for (int i = 0; i < text.Length - 1; i++)
        {
            string pair = text.Substring(i, 2);
            if (pair == "AB" || pair == "CB")
            {
                currentPairs++;
                i++; 
            }
            else
            {
                maxPairs = Math.Max(maxPairs, currentPairs);
                currentPairs = 0;
            }
        }

        maxPairs = Math.Max(maxPairs, currentPairs);
        return maxPairs;
    }
}
