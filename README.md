# Dictionary
Whether given letters make up any word from dictionary or not.



#include &lt;cstring&gt;

#include &lt;iostream&gt;

using namespace std;


#define M 3

#define N 3

string dictionary[] = { &quot;FIRE&quot;, &quot;FOR&quot;, &quot;FIGHT&quot;, &quot;FOREVER&quot; };

int n = sizeof(dictionary) / sizeof(dictionary[0]);

bool isWord(string&amp; str)

{

for (int i = 0; i &lt; n; i++)

if (str.compare(dictionary[i]) == 0)

return true;

return false;

}

void findWordsUtil(char boggle[M][N], bool visited[M][N], int i,

int j, string&amp; str)

{

visited[i][j] = true;

str = str + boggle[i][j];

if (isWord(str))

cout &lt;&lt; str &lt;&lt; endl;

for (int row = i - 1; row &lt;= i + 1 &amp;&amp; row &lt; M; row++)

for (int col = j - 1; col &lt;= j + 1 &amp;&amp; col &lt; N; col++)


if (row &gt;= 0 &amp;&amp; col &gt;= 0 &amp;&amp; !visited[row][col])

findWordsUtil(boggle, visited, row, col, str);

str.erase(str.length() - 1);

visited[i][j] = false;
}

void findWords(char boggle[M][N])

{

bool visited[M][N] = { { false } };

string str = &quot;&quot;;

for (int i = 0; i &lt; M; i++)

for (int j = 0; j &lt; N; j++)

findWordsUtil(boggle, visited, i, j, str);

}

int main()

{

char boggle[M][N] = { { &#39;G&#39;, &#39;I&#39;, &#39;R&#39; },

{ &#39;F&#39;, &#39;E&#39;, &#39;C&#39; },

{ &#39;O&#39;, &#39;V&#39;, &#39;E&#39; } };

cout &lt;&lt; &quot;Following words of dictionary are present\n&quot;;

findWords(boggle);

return 0;

}
