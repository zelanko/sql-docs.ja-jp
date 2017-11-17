---
title: "(TRANSACT-SQL) の説明 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4846a576-57ea-4068-959c-81e69e39ddc1
caps.latest.revision: 13
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: af61ec5c670bdc48a3f661080983fac3e7263014
ms.contentlocale: ja-jp
ms.lasthandoff: 10/24/2017

---
# <a name="explain-transact-sql"></a>説明 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  クエリ プランを返します、 [!INCLUDE[ssDW](../../includes/ssdw-md.md)] [!INCLUDE[DWsql](../../includes/dwsql-md.md)]せず、ステートメントを実行するステートメント。 使用して**説明**プレビューがどのような操作データの移動が必要になり、クエリ操作の推定コストを表示します。  
  
 クエリ プランの詳細についてを参照してください「クエリ プランを理解する」、[!INCLUDE[pdw-product-documentation_md](../../includes/pdw-product-documentation-md.md)]です。  
  
## <a name="syntax"></a>構文  
  

```  
EXPLAIN SQL_statement  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *SQL_statement*  
 [!INCLUDE[DWsql](../../includes/dwsql-md.md)]をステートメント**説明**実行されます。 *SQL_statement*これらのコマンドのいずれかです:**選択**、**挿入**、**更新**、**削除**、 **CREATE TABLE AS SELECT**、**リモート テーブルを作成する**です。  
  
## <a name="permissions"></a>Permissions  
 必要があります、 **SHOWPLAN**アクセス許可、および実行する権限*SQL_statement*です。 参照してください[アクセス許可: GRANT、DENY、REVOKE & #40 です。Azure SQL Data Warehouse、並列データ ウェアハウス &#41;](../../t-sql/statements/permissions-grant-deny-revoke-azure-sql-data-warehouse-parallel-data-warehouse.md).  
  
## <a name="return-value"></a>戻り値  
 戻り値、**説明**コマンドは、次に示す構造を持つ XML ドキュメントです。 この XML ドキュメントが、指定したクエリのクエリ プランのすべての操作を示してで囲まれた各、`<dsql_operation>`タグ。 型の戻り値は、 **nvarchar (max)**です。  
  
 返されたクエリ プランは、シーケンシャルな SQL ステートメントを示しています。クエリの実行時、同時実行いくつかのステートメントが順番に表示される可能性がありますので、並列化された操作を伴う場合があります。  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<dsql_query>  
  <sql>. . .</sql>  
  <params />  
  <dsql_operations>  
    <dsql_operation>  
     . . .      
    </dsql_operation>  
    [ . . . n ]  
  <dsql_operations>  
</dsql_query>  
```  
  
 XML タグは、この情報を含めます。  
  
|XML タグ|概要、属性、およびコンテンツ|  
|-------------|--------------------------------------|  
|\<dsql_query >|最上位レベル/ドキュメントの要素。|
|\<sql >|エコー *SQL_statement*です。|  
|\<params >|このタグは、この時点では使用されません。|  
|\<dsql_operations >|まとめたものし、クエリの手順が含まれています、クエリのコスト情報が含まれています。 すべて含まれています、`<dsql_operation>`ブロックします。 このタグには、全体のクエリに対して行数の情報が含まれています。<br /><br /> `<dsql_operations total_cost=total_cost total_number_operations=total_number_operations>`<br /><br /> *total_cost*推定時間 (ミリ秒) を実行するクエリの合計がします。<br /><br /> *total_number_operations*クエリの操作の合計数です。 並列に処理して複数のノード上で実行される操作は、1 つの操作としてカウントされます。|  
|\<dsql_operation >|クエリ プラン内で 1 回の操作について説明します。 \<Dsql_operation > タグに属性として操作の種類が含まれています。<br /><br /> `<dsql_operation operation_type=operation_type>`<br /><br /> *operation_type*で見つかった値の 1 つ[クエリを実行するデータ (SQL Server PDW)](http://msdn.microsoft.com/en-us/3f4f5643-012a-4c36-b5ec-691c4bbe668c)です。<br /><br /> 内のコンテンツ、`\<dsql_operation>`ブロックは操作の種類に依存します。<br /><br /> 次の表を参照してください。|  
  
|操作の種類|コンテンツ|例|  
|--------------------|-------------|-------------|  
|BROADCAST_MOVE、DISTRIBUTE_REPLICATED_TABLE_MOVE、MASTER_TABLE_MOVE、PARTITION_MOVE、SHUFFLE_MOVE、および TRIM_MOVE|`<operation_cost>`これらの属性を持つ要素。 値は、ローカル操作のみを反映します。<br /><br /> -   *コスト*ローカル オペレーター コストは、(ミリ秒) を実行する操作の推定所要時間を示します。<br />-   *accumulative_cost*ミリ秒での並列処理の加算結果の値を含むプランに見られるすべての操作の合計です。<br />-   *average_rowsize*は、行の推定平均サイズ (バイト単位) を取得および操作中に渡される行のです。<br />-   *output_rows*出力 (ノード) の基数は、出力行の数を示します。<br /><br /> `<location>`: ノードまたは分布の操作を実行します。 オプションは、:「コントロール」、"ComputeNode"、"AllComputeNodes"、"AllDistributions"、"SubsetDistributions"、「配布」および"SubsetNodes"です。<br /><br /> `<source_statement>`: ソース データを、ランダムに移動します。<br /><br /> `<destination_table>`: 内部の一時テーブルにデータが移動されます。<br /><br /> `<shuffle_columns>`: (SHUFFLE_MOVE 操作にのみ該当)。 一時テーブルのディストリビューション列として使用される 1 つまたは複数の列です。|`<operation_cost cost="40" accumulative_cost="40" average_rowsize = "50" output_rows="100"/>`<br /><br /> `<location distribution="AllDistributions" />`<br /><br /> `<source_statement type="statement">SELECT [TableAlias_3b77ee1d8ccf4a94ba644118b355db9d].[dist_date] FROM [qatest].[dbo].[flyers] [TableAlias_3b77ee1d8ccf4a94ba644118b355db9d]       </source_statement>`<br /><br /> `<destination_table>Q_[TEMP_ID_259]_[PARTITION_ID]</destination_table>`<br /><br /> `<shuffle_columns>dist_date;</shuffle_columns>`|  
|CopyOperation|`<operation_cost>`:「`<operation_cost>`上。<br /><br /> `<DestinationCatalog>`: 送信先ノードまたはノード。<br /><br /> `<DestinationSchema>`: DestinationCatalog で送信先スキーマです。<br /><br /> `<DestinationTableName>`: コピー先のテーブルまたは"TableName"の名前。<br /><br /> `<DestinationDatasource>`: 名前または接続情報の変換先データ ソース。<br /><br /> `<Username>``<Password>`: これらのフィールドを示すこと、ユーザー名とパスワード、変換先の必要があります。<br /><br /> `<BatchSize>`: コピー操作のバッチ サイズ。<br /><br /> `<SelectStatement>`: Select ステートメントのコピーを実行するために使用します。<br /><br /> `<distribution>`: コピーが実行される分布です。|`<operation_cost cost="0" accumulative_cost="0" average_rowsize="4" output_rows="1" />`<br /><br /> `<DestinationCatalog>master</DestinationCatalog>`<br /><br /> `<DestinationSchema>dbo</DestinationSchema>`<br /><br /> `<DestinationTableName>[TableName]</DestinationTableName>`<br /><br /> `<DestinationDatasource>localhost, 8080</DestinationDatasource>`<br /><br /> `<Username>...</Username>`<br /><br /> `<Password>...</Password>`<br /><br /> `<BatchSize>6000</BatchSize>`<br /><br /> `<SelectStatement>SELECT T1_1.c1 AS c1 FROM [qatest].[dbo].[gigs] AS T1_1</SelectStatement>`<br /><br /> `<distribution>ControlNode</distribution>`|  
|MetaDataCreate_Operation|`<source_table>`: 操作のソース テーブル。<br /><br /> `<destionation_table>`: 操作の変換先テーブルです。|`<source_table>databases</source_table>`<br /><br /> `<destination_table>MetaDataCreateLandingTempTable</destination_table>`|  
|ON|`<location>`:「`<location>`上。<br /><br /> `<sql_operation>`: ノードで実行される SQL コマンドを識別します。|`<location permanent="false" distribution="AllDistributions">Compute</location>`<br /><br /> `<sql_operation type="statement">CREATE TABLE [tempdb].[dbo]. [Q_[TEMP_ID_259]]_ [PARTITION_ID]]]([dist_date] DATE) WITH (DISTRIBUTION = HASH([dist_date]),) </sql_operation>`|  
|RemoteOnOperation|`<DestinationCatalog>`: 送信先のカタログ。<br /><br /> `<DestinationSchema>`: DestinationCatalog で送信先スキーマです。<br /><br /> `<DestinationTableName>`: コピー先のテーブルまたは"TableName"の名前。<br /><br /> `<DestinationDatasource>`: 変換先データ ソースの名前。<br /><br /> `<Username>``<Password>`: これらのフィールドを示すこと、ユーザー名とパスワード、変換先の必要があります。<br /><br /> `<CreateStatement>`: テーブルの作成ステートメント、移行先データベース。|`<DestinationCatalog>master</DestinationCatalog>`<br /><br /> `<DestinationSchema>dbo</DestinationSchema>`<br /><br /> `<DestinationTableName>TableName</DestinationTableName>`<br /><br /> `<DestinationDatasource>DestDataSource</DestinationDatasource>`<br /><br /> `<Username>...</Username>`<br /><br /> `<Password>...</Password>`<br /><br /> `<CreateStatement>CREATE TABLE [master].[dbo].[TableName] ([col1] BIGINT) ON [PRIMARY] WITH(DATA_COMPRESSION=PAGE);</CreateStatement>`|  
|RETURN|`<resultset>`: 結果セットの識別子。|`<resultset>RS_19</resultset>`|  
|RND_ID|`<identifier>`: 作成したオブジェクトの識別子。|`<identifier>TEMP_ID_260</identifier>`|  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 **説明**に適用できます*最適化*の結果に基づいて、クエリでのみ、向上または変更できるクエリである、**説明**コマンド。 サポートされている**説明**上に示されたコマンド。 使用しようとしています。**説明**サポートされていないクエリを使用して型はエラーを返しますまたは、クエリをエコーします。  
  
 **説明**ユーザー トランザクションでサポートされていません。  
  
## <a name="examples"></a>使用例  
 次の例は、**説明**でコマンドを実行、**選択**ステートメント、および XML の結果。  
  
 **説明文を送信します。**  
  
 この例で送信されたコマンドです。  
  
```  
-- Uses AdventureWorks  
  
EXPLAIN   
    SELECT CAST (AVG(YearlyIncome) AS int) AS AverageIncome,   
        CAST(AVG(FIS.SalesAmount) AS int) AS AverageSales,   
        G.StateProvinceName, T.SalesTerritoryGroup  
    FROM dbo.DimGeography AS G  
    JOIN dbo.DimSalesTerritory AS T  
        ON G.SalesTerritoryKey = T.SalesTerritoryKey  
    JOIN dbo.DimCustomer AS C  
        ON G.GeographyKey = C.GeographyKey  
    JOIN dbo.FactInternetSales AS FIS  
        ON C.CustomerKey = FIS.CustomerKey  
    WHERE T.SalesTerritoryGroup IN ('North America', 'Pacific')  
        AND Gender = 'F'  
    GROUP BY G.StateProvinceName, T.SalesTerritoryGroup  
    ORDER BY AVG(YearlyIncome) DESC;  
GO  
```  
  
 使用して、ステートメントを実行した後、**説明**オプション、[メッセージ] タブには、という名前の単一行**説明**、XML 文字で始まると`\<?xml version="1.0" encoding="utf-8"?>`XML 内のテキスト全体を開くとをクリックして、XML のウィンドウです。 次のコメントをより深く理解するには、には、SSDT での行番号の表示をオンにする必要があります。  
  
#### <a name="to-turn-on-line-numbers"></a>行番号を有効にするには  
  
1.  表示される出力と、**説明**の SSDT では、tab キー、**ツール**メニューの **オプション**です。  
  
2.  展開、**テキスト エディター**セクションで、展開**XML**、クリックして**全般**です。  
  
3.  **表示**領域で、チェック**行番号**です。  
  
4.  **[OK]**をクリックします。  
  
 **説明の出力の例**  
  
 XML の結果、**説明**コマンドをオンになっている行番号です。  
  
```  
1  \<?xml version="1.0" encoding="utf-8"?>  
2  <dsql_query>  
3    <sql>SELECT CAST (AVG(YearlyIncome) AS int) AS AverageIncome,   
4          CAST(AVG(FIS.SalesAmount) AS int) AS AverageSales,   
5          G.StateProvinceName, T.SalesTerritoryGroup  
6      FROM dbo.DimGeography AS G  
7      JOIN dbo.DimSalesTerritory AS T  
8          ON G.SalesTerritoryKey = T.SalesTerritoryKey  
9      JOIN dbo.DimCustomer AS C  
10          ON G.GeographyKey = C.GeographyKey  
11      JOIN dbo.FactInternetSales AS FIS  
12          ON C.CustomerKey = FIS.CustomerKey  
13      WHERE T.SalesTerritoryGroup IN ('North America', 'Pacific')  
14          AND Gender = 'F'  
15      GROUP BY G.StateProvinceName, T.SalesTerritoryGroup  
16      ORDER BY AVG(YearlyIncome) DESC</sql>  
17    <dsql_operations total_cost="0.926237696" total_number_operations="9">  
18      <dsql_operation operation_type="RND_ID">  
19        <identifier>TEMP_ID_16893</identifier>  
20      </dsql_operation>  
21      <dsql_operation operation_type="ON">  
22        <location permanent="false" distribution="AllComputeNodes" />  
23        <sql_operations>  
24          <sql_operation type="statement">CREATE TABLE [tempdb].[dbo].[TEMP_ID_16893] ([CustomerKey] INT NOT NULL, [GeographyKey] INT, [YearlyIncome] MONEY ) WITH(DATA_COMPRESSION=PAGE);</sql_operation>  
25        </sql_operations>  
26      </dsql_operation>  
27      <dsql_operation operation_type="BROADCAST_MOVE">  
28        <operation_cost cost="0.121431552" accumulative_cost="0.121431552" average_rowsize="16" output_rows="31.6228" />  
29        <source_statement>SELECT [T1_1].[CustomerKey] AS [CustomerKey],  
30         [T1_1].[GeographyKey] AS [GeographyKey],  
31         [T1_1].[YearlyIncome] AS [YearlyIncome]  
32  FROM   (SELECT [T2_1].[CustomerKey] AS [CustomerKey],  
33                 [T2_1].[GeographyKey] AS [GeographyKey],  
34                 [T2_1].[YearlyIncome] AS [YearlyIncome]  
35          FROM   [AdventureWorksPDW2012].[dbo].[DimCustomer] AS T2_1  
36          WHERE  ([T2_1].[Gender] = CAST (N'F' COLLATE Latin1_General_100_CI_AS_KS_WS AS NVARCHAR (1)) COLLATE Latin1_General_100_CI_AS_KS_WS)) AS T1_1</source_statement>  
37        <destination_table>[TEMP_ID_16893]</destination_table>  
38      </dsql_operation>  
39      <dsql_operation operation_type="RND_ID">  
40        <identifier>TEMP_ID_16894</identifier>  
41      </dsql_operation>  
42      <dsql_operation operation_type="ON">  
43        <location permanent="false" distribution="AllDistributions" />  
44        <sql_operations>  
45          <sql_operation type="statement">CREATE TABLE [tempdb].[dbo].[TEMP_ID_16894] ([StateProvinceName] NVARCHAR(50) COLLATE Latin1_General_100_CI_AS_KS_WS, [SalesTerritoryGroup] NVARCHAR(50) COLLATE Latin1_General_100_CI_AS_KS_WS NOT NULL, [col] BIGINT, [col1] MONEY NOT NULL, [col2] BIGINT, [col3] MONEY NOT NULL ) WITH(DATA_COMPRESSION=PAGE);</sql_operation>  
46        </sql_operations>  
47      </dsql_operation>  
48      <dsql_operation operation_type="SHUFFLE_MOVE">  
49        <operation_cost cost="0.804806144" accumulative_cost="0.926237696" average_rowsize="232" output_rows="108.406" />  
50        <source_statement>SELECT [T1_1].[StateProvinceName] AS [StateProvinceName],  
51         [T1_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
52         [T1_1].[col2] AS [col],  
53         [T1_1].[col] AS [col1],  
54         [T1_1].[col3] AS [col2],  
55         [T1_1].[col1] AS [col3]  
56  FROM   (SELECT ISNULL([T2_1].[col1], CONVERT (MONEY, 0.00, 0)) AS [col],  
57                 ISNULL([T2_1].[col3], CONVERT (MONEY, 0.00, 0)) AS [col1],  
58                 [T2_1].[StateProvinceName] AS [StateProvinceName],  
59                 [T2_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
60                 [T2_1].[col] AS [col2],  
61                 [T2_1].[col2] AS [col3]  
62          FROM   (SELECT   COUNT_BIG([T3_2].[YearlyIncome]) AS [col],  
63                           SUM([T3_2].[YearlyIncome]) AS [col1],  
64                           COUNT_BIG(CAST ((0) AS INT)) AS [col2],  
65                           SUM([T3_2].[SalesAmount]) AS [col3],  
66                           [T3_2].[StateProvinceName] AS [StateProvinceName],  
67                           [T3_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
68                  FROM     (SELECT [T4_1].[SalesTerritoryKey] AS [SalesTerritoryKey],  
69                                   [T4_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
70                            FROM   [AdventureWorksPDW2012].[dbo].[DimSalesTerritory] AS T4_1  
71                            WHERE  (([T4_1].[SalesTerritoryGroup] = CAST (N'North America' COLLATE Latin1_General_100_CI_AS_KS_WS AS NVARCHAR (13)) COLLATE Latin1_General_100_CI_AS_KS_WS)  
72                                    OR ([T4_1].[SalesTerritoryGroup] = CAST (N'Pacific' COLLATE Latin1_General_100_CI_AS_KS_WS AS NVARCHAR (7)) COLLATE Latin1_General_100_CI_AS_KS_WS))) AS T3_1  
73                           INNER JOIN  
74                           (SELECT [T4_1].[SalesTerritoryKey] AS [SalesTerritoryKey],  
75                                   [T4_2].[YearlyIncome] AS [YearlyIncome],  
76                                   [T4_2].[SalesAmount] AS [SalesAmount],  
77                                   [T4_1].[StateProvinceName] AS [StateProvinceName]  
78                            FROM   [AdventureWorksPDW2012].[dbo].[DimGeography] AS T4_1  
79                                   INNER JOIN  
80                                   (SELECT [T5_2].[GeographyKey] AS [GeographyKey],  
81                                           [T5_2].[YearlyIncome] AS [YearlyIncome],  
82                                           [T5_1].[SalesAmount] AS [SalesAmount]  
83                                    FROM   [AdventureWorksPDW2012].[dbo].[FactInternetSales] AS T5_1  
84                                           INNER JOIN  
85                                           [tempdb].[dbo].[TEMP_ID_16893] AS T5_2  
86                                           ON ([T5_1].[CustomerKey] = [T5_2].[CustomerKey])) AS T4_2  
87                                   ON ([T4_2].[GeographyKey] = [T4_1].[GeographyKey])) AS T3_2  
88                           ON ([T3_1].[SalesTerritoryKey] = [T3_2].[SalesTerritoryKey])  
89                  GROUP BY [T3_2].[StateProvinceName], [T3_1].[SalesTerritoryGroup]) AS T2_1) AS T1_1</source_statement>  
90        <destination_table>[TEMP_ID_16894]</destination_table>  
91        <shuffle_columns>StateProvinceName;</shuffle_columns>  
92      </dsql_operation>  
93      <dsql_operation operation_type="ON">  
94        <location permanent="false" distribution="AllComputeNodes" />  
95        <sql_operations>  
96          <sql_operation type="statement">DROP TABLE [tempdb].[dbo].[TEMP_ID_16893]</sql_operation>  
97        </sql_operations>  
98      </dsql_operation>  
99      <dsql_operation operation_type="RETURN">  
100        <location distribution="AllDistributions" />  
101        <select>SELECT   [T1_1].[col] AS [col],  
102           [T1_1].[col1] AS [col1],  
103           [T1_1].[StateProvinceName] AS [StateProvinceName],  
104           [T1_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
105           [T1_1].[col2] AS [col2]  
106  FROM     (SELECT CONVERT (INT, [T2_1].[col], 0) AS [col],  
107                   CONVERT (INT, [T2_1].[col1], 0) AS [col1],  
108                   [T2_1].[StateProvinceName] AS [StateProvinceName],  
109                   [T2_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup],  
110                   [T2_1].[col] AS [col2]  
111            FROM   (SELECT CASE  
112                            WHEN ([T3_1].[col] = CAST ((0) AS BIGINT)) THEN CAST (NULL AS MONEY)  
113                            ELSE ([T3_1].[col1] / CONVERT (MONEY, [T3_1].[col], 0))  
114                           END AS [col],  
115                           CASE  
116                            WHEN ([T3_1].[col2] = CAST ((0) AS BIGINT)) THEN CAST (NULL AS MONEY)  
117                            ELSE ([T3_1].[col3] / CONVERT (MONEY, [T3_1].[col2], 0))  
118                           END AS [col1],  
119                           [T3_1].[StateProvinceName] AS [StateProvinceName],  
120                           [T3_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
121                    FROM   (SELECT ISNULL([T4_1].[col], CONVERT (BIGINT, 0, 0)) AS [col],  
122                                   ISNULL([T4_1].[col1], CONVERT (MONEY, 0.00, 0)) AS [col1],  
123                                   ISNULL([T4_1].[col2], CONVERT (BIGINT, 0, 0)) AS [col2],  
124                                   ISNULL([T4_1].[col3], CONVERT (MONEY, 0.00, 0)) AS [col3],  
125                                   [T4_1].[StateProvinceName] AS [StateProvinceName],  
126                                   [T4_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
127                            FROM   (SELECT   SUM([T5_1].[col]) AS [col],  
128                                             SUM([T5_1].[col1]) AS [col1],  
129                                             SUM([T5_1].[col2]) AS [col2],  
130                                             SUM([T5_1].[col3]) AS [col3],  
131                                             [T5_1].[StateProvinceName] AS [StateProvinceName],  
132                                             [T5_1].[SalesTerritoryGroup] AS [SalesTerritoryGroup]  
133                                    FROM     [tempdb].[dbo].[TEMP_ID_16894] AS T5_1  
134                                    GROUP BY [T5_1].[StateProvinceName], [T5_1].[SalesTerritoryGroup]) AS T4_1) AS T3_1) AS T2_1) AS T1_1  
135  ORDER BY [T1_1].[col2] DESC</select>  
136      </dsql_operation>  
137      <dsql_operation operation_type="ON">  
138        <location permanent="false" distribution="AllDistributions" />  
139        <sql_operations>  
140          <sql_operation type="statement">DROP TABLE [tempdb].[dbo].[TEMP_ID_16894]</sql_operation>  
141        </sql_operations>  
142      </dsql_operation>  
143    </dsql_operations>  
144  </dsql_query>  
  
```  
  
 **説明の出力の意味**  
  
 上記の出力には、番号付き 144 の行が含まれています。 このクエリからの出力結果は若干異なる場合があります。 次の一覧では、重要なセクションについて説明します。  
  
-   行 3 から 16 までは、分析するクエリの説明を提供します。  
  
-   17 を行、操作の合計数は 9 になるように指定します。 によって、単語の各操作の開始を検索する**dsql_operation**です。  
  
-   18 行目では、1 の操作を開始します。 行 18、19 に示す、 **RND_ID**操作は、オブジェクトの説明に使用されるランダムな ID 番号を作成します。 上記の出力で説明されているオブジェクトが**TEMP_ID_16893**です。 お客様の番号が変更されます。  
  
-   20 行目では、2 の操作を開始します。 行から 25 までの 21: すべてのコンピューティング ノード、という名前の一時テーブルを作成する**TEMP_ID_16893**です。  
  
-   26 の行は、3 の操作を開始します。 行 27 37 ~: データの移動**TEMP_ID_16893**ブロードキャスト move を使用しています。 各計算ノードに送信されるクエリが提供されます。 37 の行では、コピー先のテーブルを指定**TEMP_ID_16893**です。  
  
-   38 行目では、4 の操作を開始します。 線の 40 を通じて 39: テーブルのランダムな ID を作成します。 **TEMP_ID_16894**上記の例の ID 番号です。 お客様の番号が変更されます。  
  
-   行 41 では、5 の操作を開始します。 行 46 を通じて 42: すべてのノードで、という名前の一時テーブルを作成します。 **TEMP_ID_16894**です。  
  
-   47 の行は、6 の操作を開始します。 行の値が 91 から 48: さまざまなテーブルからデータを移動 (など**TEMP_ID_16893**) テーブルに**TEMP_ID_16894**、ランダム再生を使用して、操作を移動します。 各計算ノードに送信されるクエリが提供されます。 行 90 と変換先テーブルを指定する**TEMP_ID_16894**です。 行の値が 91年では、列を指定します。  
  
-   行 92年 7 の操作を開始します。 97 を通じて行 93年: すべてのコンピューティング ノード、一時テーブルを削除**TEMP_ID_16893**です。  
  
-   行 98年では、8 の操作を開始します。 135 を介して行 99年: クライアントに結果を返します。 結果を取得する指定したクエリを使用します。  
  
-   行 136 では、9 の操作を開始します。 行 140 を通じて 137: すべてのノードに一時テーブルの削除**TEMP_ID_16894**です。  
  
  


