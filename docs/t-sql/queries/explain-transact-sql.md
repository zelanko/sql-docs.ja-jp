---
title: EXPLAIN (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4846a576-57ea-4068-959c-81e69e39ddc1
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 9962b3a24c8a19ff253d22c28779259bcb1f292a
ms.sourcegitcommit: b8e2e3e6e04368aac54100c403cc15fd4e4ec13a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45564068"
---
# <a name="explain-transact-sql"></a>EXPLAIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  [!INCLUDE[ssDW](../../includes/ssdw-md.md)] [!INCLUDE[DWsql](../../includes/dwsql-md.md)] ステートメントを実行せずに、ステートメントのクエリ プランを返します。 **EXPLAIN** を使用して、どの操作でデータの移動が必要になるかをプレビューし、クエリ操作の推定コストを表示します。  
  
 クエリ プランの詳細については、[!INCLUDE[pdw-product-documentation_md](../../includes/pdw-product-documentation-md.md)]にある「Understanding Query Plans」 (クエリ プランについて) を参照してください。  
  
## <a name="syntax"></a>構文  
  

```  
EXPLAIN SQL_statement  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *SQL_statement*  
 **EXPLAIN** を実行する [!INCLUDE[DWsql](../../includes/dwsql-md.md)] ステートメントです。 *SQL_statement* には、**SELECT**、**INSERT**、**UPDATE**、**DELETE**、**CREATE TABLE AS SELECT**、**CREATE REMOTE TABLE** のいずれかのコマンドが使用できます。  
  
## <a name="permissions"></a>アクセス許可  
 **SHOWPLAN** アクセス許可と、*SQL_statement* を実行するためのアクセス許可が必要です。 「[アクセス許可: GRANT、DENY、REVOKE &#40;Azure SQL Data Warehouse、並列データ ウェアハウス&#41;](../../t-sql/statements/permissions-grant-deny-revoke-azure-sql-data-warehouse-parallel-data-warehouse.md)」を参照してください。  
  
## <a name="return-value"></a>戻り値  
 **EXPLAIN** コマンドからの戻り値は、次に示す構造を持つ XML ドキュメントです。 この XML ドキュメントには、指定したクエリのクエリ プランのすべての操作が、それぞれ `<dsql_operation>` タグで囲まれて一覧表示されます。 戻り値の型は **nvarchar (max)** です。  
  
 返されたクエリ プランは、シーケンシャル SQL ステートメントを表現します。クエリの実行時、並列化された操作を伴う場合があるため、表示されている一部のシーケンシャル ステートメントが同時に実行される可能性があります。  
  
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
  
 XML タグには、次の情報が含まれます。  
  
|XML タグ|概要、属性、およびコンテンツ|  
|-------------|--------------------------------------|  
|\<dsql_query>|最上位レベル/ドキュメントの要素。|
|\<sql>|*SQL_statement* をエコーします。|  
|\<params>|このタグは、この時点では使用されません。|  
|\<dsql_operations>|クエリの手順がまとめられて含まれ、クエリのコスト情報が含まれます。 すべての `<dsql_operation>` ブロックも含まれます。 このタグには、全体のクエリのカウント情報が含まれています。<br /><br /> `<dsql_operations total_cost=total_cost total_number_operations=total_number_operations>`<br /><br /> *total_cost* は、クエリの実行にかかる推定合計時間 (ミリ秒) です。<br /><br /> *total_number_operations* は、クエリの操作の総数です。 並列化され複数のノードで実行される操作は、1 つの操作としてカウントされます。|  
|\<dsql_operation>|クエリ プラン内の 1 つの操作について説明します。 \<dsql_operation> タグには、属性として操作の種類が含まれます。<br /><br /> `<dsql_operation operation_type=operation_type>`<br /><br /> *operation_type* は、[データのクエリ (SQL Server PDW)](http://msdn.microsoft.com/3f4f5643-012a-4c36-b5ec-691c4bbe668c) で見つかった値の 1 つです。<br /><br /> `\<dsql_operation>` ブロック内のコンテンツは、操作の種類によって異なります。<br /><br /> 次の表を参照してください。|  
  
|操作の種類|コンテンツ|例|  
|--------------------|-------------|-------------|  
|BROADCAST_MOVE、DISTRIBUTE_REPLICATED_TABLE_MOVE、MASTER_TABLE_MOVE、PARTITION_MOVE、SHUFFLE_MOVE、および TRIM_MOVE|これらの属性を持つ `<operation_cost>` 要素。 値には、ローカル操作のみが反映されます。<br /><br /> -   *cost* は、ローカル オペレーター コストで、実行する操作の推定所要時間 (ミリ秒) を示します。<br />-   *accumulative_cost* は、プランで見られるすべての操作 (並列処理の合計値を含む) の合計です (ミリ秒)。<br />-   *average_rowsize*は、操作中に取得されて渡される行の推定平均サイズ (バイト) です。<br />-   *output_rows* は、出力 (ノード) カーディナリティで、出力行の数を示します。<br /><br /> `<location>`: 操作が実行されるノードまたはディストリビューション。 オプション: “Control”、"ComputeNode"、"AllComputeNodes"、"AllDistributions"、"SubsetDistributions"、"Distribution"、および "SubsetNodes"。<br /><br /> `<source_statement>`: SHUFFLE_MOVE のソース データ。<br /><br /> `<destination_table>`: データの移動先となる内部の一時テーブル。<br /><br /> `<shuffle_columns>`: (SHUFFLE_MOVE 操作にのみ適用可能)。 一時テーブルのディストリビューション列として使用される 1 つまたは複数の列。|`<operation_cost cost="40" accumulative_cost="40" average_rowsize = "50" output_rows="100"/>`<br /><br /> `<location distribution="AllDistributions" />`<br /><br /> `<source_statement type="statement">SELECT [TableAlias_3b77ee1d8ccf4a94ba644118b355db9d].[dist_date] FROM [qatest].[dbo].[flyers] [TableAlias_3b77ee1d8ccf4a94ba644118b355db9d]       </source_statement>`<br /><br /> `<destination_table>Q_[TEMP_ID_259]_[PARTITION_ID]</destination_table>`<br /><br /> `<shuffle_columns>dist_date;</shuffle_columns>`|  
|CopyOperation|`<operation_cost>`: 上記の `<operation_cost>` を参照。<br /><br /> `<DestinationCatalog>`: 宛先ノード。<br /><br /> `<DestinationSchema>`: DestinationCatalog 内の宛先スキーマ。<br /><br /> `<DestinationTableName>`: 宛先テーブルの名前または “TableName”。<br /><br /> `<DestinationDatasource>`: 宛先データベースの接続の名前または情報。<br /><br /> `<Username>` と `<Password>`: これらのフィールドには、宛先で必要となるユーザー名とパスワードが示されます。<br /><br /> `<BatchSize>`: コピー操作のバッチ サイズ。<br /><br /> `<SelectStatement>`: コピーを実行するために使用される Select ステートメント。<br /><br /> `<distribution>`: コピーが実行されるディストリビューション。|`<operation_cost cost="0" accumulative_cost="0" average_rowsize="4" output_rows="1" />`<br /><br /> `<DestinationCatalog>master</DestinationCatalog>`<br /><br /> `<DestinationSchema>dbo</DestinationSchema>`<br /><br /> `<DestinationTableName>[TableName]</DestinationTableName>`<br /><br /> `<DestinationDatasource>localhost, 8080</DestinationDatasource>`<br /><br /> `<Username>...</Username>`<br /><br /> `<Password>...</Password>`<br /><br /> `<BatchSize>6000</BatchSize>`<br /><br /> `<SelectStatement>SELECT T1_1.c1 AS c1 FROM [qatest].[dbo].[gigs] AS T1_1</SelectStatement>`<br /><br /> `<distribution>ControlNode</distribution>`|  
|MetaDataCreate_Operation|`<source_table>`: 操作のソース テーブル。<br /><br /> `<destionation_table>`: 操作の宛先テーブル。|`<source_table>databases</source_table>`<br /><br /> `<destination_table>MetaDataCreateLandingTempTable</destination_table>`|  
|ON|`<location>`: 上記の `<location>` を参照。<br /><br /> `<sql_operation>`: ノードで実行される SQL コマンドを識別します。|`<location permanent="false" distribution="AllDistributions">Compute</location>`<br /><br /> `<sql_operation type="statement">CREATE TABLE [tempdb].[dbo]. [Q_[TEMP_ID_259]]_ [PARTITION_ID]]]([dist_date] DATE) WITH (DISTRIBUTION = HASH([dist_date]),) </sql_operation>`|  
|RemoteOnOperation|`<DestinationCatalog>`: 宛先カタログ。<br /><br /> `<DestinationSchema>`: DestinationCatalog 内の宛先スキーマ。<br /><br /> `<DestinationTableName>`: 宛先テーブルの名前または “TableName”。<br /><br /> `<DestinationDatasource>`: 宛先データソースの名前。<br /><br /> `<Username>` と `<Password>`: これらのフィールドには、宛先で必要となるユーザー名とパスワードが示されます。<br /><br /> `<CreateStatement>`: 宛先データベースのテーブルの作成ステートメント。|`<DestinationCatalog>master</DestinationCatalog>`<br /><br /> `<DestinationSchema>dbo</DestinationSchema>`<br /><br /> `<DestinationTableName>TableName</DestinationTableName>`<br /><br /> `<DestinationDatasource>DestDataSource</DestinationDatasource>`<br /><br /> `<Username>...</Username>`<br /><br /> `<Password>...</Password>`<br /><br /> `<CreateStatement>CREATE TABLE [master].[dbo].[TableName] ([col1] BIGINT) ON [PRIMARY] WITH(DATA_COMPRESSION=PAGE);</CreateStatement>`|  
|RETURN|`<resultset>`: 結果セットの識別子。|`<resultset>RS_19</resultset>`|  
|RND_ID|`<identifier>`: 作成したオブジェクトの識別子。|`<identifier>TEMP_ID_260</identifier>`|  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 **EXPLAIN** は、*最適化可能な*クエリ、つまり、**EXPLAIN** コマンドの結果に基づいて、改善または修正できるクエリにのみ適用できます。 上記に一覧表示されている **EXPLAIN** コマンドがサポートされています。 **EXPLAIN** をサポートされていないクエリの型で使用しようとすると、エラーが返されるか、クエリがエコーされます。  
  
 **EXPLAIN** はユーザー トランザクションではサポートされていません。  
  
## <a name="examples"></a>使用例  
 次の例では、**SELECT**ステートメントで実行される **EXPLAIN** コマンドと、XML 結果を示します。  
  
 **EXPLAIN ステートメントの送信**  
  
 この例で送信されたコマンド次のとおりです。  
  
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
  
 **EXPLAIN** オプションを使用してステートメントを実行すると、メッセージ タブに **explain** という 1 行のタイトルと、`\<?xml version="1.0" encoding="utf-8"?>` で始まる XML テキストが示されます。XML をクリックすると、XML ウィンドウが開き、テキスト全体が表示されます。 次のコメントをより深く理解するには、SSDT で行番号の表示をオンにする必要があります。  
  
#### <a name="to-turn-on-line-numbers"></a>行番号を表示するには  
  
1.  SSDT の **[explain]** タブに出力が表示されている状態で、**[ツール]** メニューの **[オプション]** を選択します。  
  
2.  **[テキスト エディター]** セクションを拡大して **XML** を展開し、**[全般]** をクリックします。  
  
3.  **[表示]** 領域で、**[行番号]** をオンにします。  
  
4.  **[OK]** をクリックします。  
  
 **EXPLAIN の出力例**  
  
 **EXPLAIN** コマンドの行番号が表示された XML 結果を次に示します。  
  
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
  
 **EXPLAIN 出力の意味**  
  
 上記の出力には、144 の番号付きの行が含まれています。 実際の出力は、このクエリの出力結果とは若干異なる場合があります。 重要なセクションについて次のリストで説明します。  
  
-   行 3 から 16 は、分析するクエリの説明を提供しています。  
  
-   行 17 では、操作の合計数が 9 になるように指定しています。 各操作の開始は、**dsql_operation** という単語を検索することで見つけられます。  
  
-   行 18 から操作 1 が始まります。 行 18 と 19 は、**RND_ID** 操作により、オブジェクトの説明に使用されるランダムな ID 番号が作成されることを示しています。 上記の出力で説明されているオブジェクトは、**TEMP_ID_16893** です。 実際の番号は異なる場合があります。  
  
-   行 20 から操作 2 が始まります。 行 21 から 25: すべての計算ノードで、**TEMP_ID_16893** という名前の一時テーブルを作成します。  
  
-   行 26 から操作 3 が始まります。 行 27 から 37: BROADCAST_MOVE を使用して、データを **TEMP_ID_16893** に移動します。 各計算ノードに送信されるクエリが提供されます。 行 37 では、宛先テーブルを **TEMP_ID_16893** として指定します。  
  
-   行 38 から操作 4 が始まります。 行 39 から 40: テーブルのランダムな ID を作成します。 **TEMP_ID_16894** は、上記の例の ID 番号です。 実際の番号は異なる場合があります。  
  
-   行 41 から操作 5 が始まります。 行 42 から 46: すべてのノードで、**TEMP_ID_16894** という名前の一時テーブルを作成します。  
  
-   行 47 から操作 6 が始まります。 行 48 から 91: SHUFFLE_MOVE 操作を使用して、さまざまなテーブル (**TEMP_ID_16893** など) からテーブル **TEMP_ID_16894** にデータを移動します。 各計算ノードに送信されるクエリが提供されます。 行 90 では、宛先テーブルを **TEMP_ID_16894** として指定します。 行 91 では、列を指定します。  
  
-   行 92 から操作 7 が始まります。 行 93 から 97: すべての計算ノードで、**TEMP_ID_16893** という名前の一時テーブルを破棄します。  
  
-   行 98 から操作 8 が始まります。 行 99 から 135: クライアントに結果を返します。 指定したクエリを使用して結果を取得します。  
  
-   行 136 から操作 9 が始まります。 行 137 から 140: すべてのノードで、一時テーブル **TEMP_ID_16894** を破棄します。  
  
  

