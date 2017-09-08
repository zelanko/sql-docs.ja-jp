---
title: "照合順序 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLLATE
- COLLATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], COLLATE clause
- COLLATE clause
ms.assetid: 76763ac8-3e0d-4bbb-aa53-f5e7da021daa
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9154d293ca5b7737a9c80fef0754dcec6e461a46
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="collations"></a>照合順序
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベース定義または列定義に適用して照合順序を定義したり、文字列式に適用して照合順序キャストを適用することができる句です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
COLLATE { <collation_name> | database_default }  
<collation_name> :: =   
     { Windows_collation_name } | { SQL_collation_name }  
```  
  
## <a name="arguments"></a>引数  
 *collation_name*  
 式、列定義、またはデータベース定義に適用する照合順序の名前を指定します。 *collation_name*できますのみ指定*Windows_collation_name*または*SQL_collation_name*です。 *collation_name*リテラル値でなければなりません。 *collation_name*変数または式で表されることはできません。  
  
 *Windows_collation_name*の照合順序名には、 [Windows 照合順序名](../../t-sql/statements/windows-collation-name-transact-sql.md)です。  
  
 *SQL_collation_name*の照合順序名には、 [SQL Server 照合順序名](../../t-sql/statements/sql-server-collation-name-transact-sql.md)です。  
  
 データベース定義レベルで照合順序を適用している場合、Unicode 専用の Windows 照合順序を COLLATE 句で使用することはできません。  
  
 **database_default**  
 COLLATE 句によって、現在のデータベースの照合順序が継承されます。  
  
## <a name="remarks"></a>解説  
 COLLATE 句は、さまざまなレベルで指定できます。 その一部を次に示します。  
  
1.  データベースの作成または変更  
  
     CREATE DATABASE または ALTER DATABASE ステートメントの COLLATE 句を使用して、データベースの既定の照合順序を指定できます。 使用してデータベースを作成するときに、照合順序を指定することも[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。 照合順序を指定しない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの既定の照合順序がデータベースに指定されます。  
  
    > [!NOTE]  
    >  Windows Unicode 専用の照合順序のみ使用できます、COLLATE 句で照合順序を適用する、 **nchar**、 **nvarchar**、および**ntext**列レベルでのデータ型と式レベルのデータです。それらは、データベースまたはサーバー インスタンスの照合順序を変更する COLLATE 句で使用できません。  
  
2.  テーブル列の作成または変更  
  
     CREATE TABLE または ALTER TABLE ステートメントの COLLATE 句を使用して、文字型の各列に対して照合順序を指定できます。 使用してテーブルを作成するときに、照合順序を指定することも[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。 照合順序を指定しない場合、列には、データベースの既定の照合順序が指定されます。  
  
     使用することも、 `database_default` COLLATE 句内のオプションの代わりに、接続の一時的なテーブルの列が現在のユーザー データベースの既定の照合順序を使用するように指定に**tempdb**です。  
  
3.  式の照合順序のキャスト  
  
     COLLATE 句を使用して、文字式を特定の照合順序に適用できます。 文字リテラルと変数には、現在のデータベースの既定の照合順序が指定されます。 列参照には、列の既定の照合順序が指定されます。  
  
 識別子の照合順序は、識別子が定義されているレベルによって異なります。 ログイン名やデータベース名など、インスタンスレベルのオブジェクトの識別子には、インスタンスの既定の照合順序が指定されます。 テーブル名、ビュー名、列名など、データベース内のオブジェクトの識別子には、データベースの既定の照合順序が指定されます。 たとえば、大文字と小文字においてのみ名前が異なる 2 つのテーブルを作成する場合、大文字と小文字が区別される照合順序が指定されたデータベースでは作成できますが、大文字と小文字が区別されない照合順序が指定されたデータベースでは作成できません。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
 接続コンテキストが 1 つのデータベースに関連付けられたときに変数、GOTO ラベル、一時ストアド プロシージャおよび一時テーブルを作成し、コンテキストを別のデータベースに切り替えたときに、それらを参照することができます。 変数、GOTO ラベル、一時ストアド プロシージャ、および一時テーブルの各識別子は、サーバー インスタンスの既定の照合順序に従います。  
  
 COLLATE 句に対してのみ適用できる、 **char**、 **varchar**、**テキスト**、 **nchar**、 **nvarchar**、および**ntext**データ型。  
  
 COLLATE は*collate_name*に SQL Server 照合順序または式、列定義、またはデータベース定義に適用する Windows 照合順序のいずれかの名前を参照します。 *collation_name*できますのみ指定*Windows_collation_name*または*SQL_collation_name*パラメーターは、リテラル値を含める必要があります。 *collation_name*変数または式で表されることはできません。  
  
 照合順序は、通常、照合順序名によって識別します。ただし、セットアップ時は例外です。 セットアップ時には、Windows 照合順序にルート照合順序指定子 (照合ロケール) を指定してから、大文字と小文字の区別やアクセントの区別に関する並べ替えオプションを指定します。  
  
 システム関数を実行できる[fn_helpcollations](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md) Windows 照合順序および照合順序の SQL Server のすべての有効な照合順序名の一覧を取得します。  
  
```  
SELECT name, description  
FROM fn_helpcollations();  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]基になるオペレーティング システムでサポートされているコード ページのみをサポートできます。 照合順序に依存する動作を実行すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]参照先のオブジェクトによって使用される照合順序は、コンピューターで実行されているオペレーティング システムでサポートされているコード ページを使用する必要があります。 このようなアクションには、次のものがあります。  
  
-   データベースの作成または変更時に、データベースの既定の照合順序を指定する。  
  
-   テーブルの作成または変更時に、列の照合順序を指定する。  
  
-   復元またはアタッチ、データベース、データベースの既定の照合順序、および任意の照合順序と**char**、 **varchar**、および**テキスト**列またはデータベース内のパラメーターオペレーティング システムでサポートする必要があります。  
  
     コード ページ変換はサポートされて**char**と**varchar**データ型のではなく**テキスト**データ型。 コード ページ変換時のデータ損失はレポートされません。  
  
 指定された照合順序または参照先のオブジェクトによって使用される照合順序は、Windows でサポートされていないコード ページを使用している場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラーが表示されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-specifying-collation-during-a-select"></a>A. 選択時に照合順序を指定する  
 次の例では、単純なテーブルを作成し、4 つの行を挿入します。 例が、そのテーブルからデータを選択するときに、2 つの照合順序を適用し、デモンストレーション方法`Chiapas`は異なる方法で並べ替えられます。  
  
```tsql  
CREATE TABLE Locations  
(Place varchar(15) NOT NULL);  
GO  
INSERT Locations(Place) VALUES ('Chiapas'),('Colima')  
                             , ('Cinco Rios'), ('California');  
GO  
--Apply an typical collation  
SELECT Place FROM Locations  
ORDER BY Place  
COLLATE Latin1_General_CS_AS_KS_WS ASC;  
GO  
-- Apply a Spanish collation  
SELECT Place FROM Locations  
ORDER BY Place  
COLLATE Traditional_Spanish_ci_ai ASC;  
GO  
```  
  
 最初のクエリからの結果を次に示します。  
  
 `Place`  
  
 `-------------`  
  
 `California`  
  
 `Chiapas`  
  
 `Cinco Rios`  
  
 `Colima`  
  
 2 番目のクエリからの結果を次に示します。  
  
 `Place`  
  
 `-------------`  
  
 `California`  
  
 `Cinco Rios`  
  
 `Colima`  
  
 `Chiapas`  
  
### <a name="b-additional-examples"></a>B. その他の例  
 使用するその他の例の**COLLATE**を参照してください[CREATE DATABASE & #40 です。SQL Server TRANSACT-SQL &#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)例**G. データベースを作成し、照合順序名とオプションを指定する**、および[ALTER TABLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-table-transact-sql.md)例**列の照合順序を変更する V.**です。  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [照合順序と Unicode のサポート](../../relational-databases/collations/collation-and-unicode-support.md)   
 [照合順序の優先順位 &#40;Transact-SQL&#41;](../../t-sql/statements/collation-precedence-transact-sql.md)   
 [定数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/constants-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [テーブルと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/table-transact-sql.md)  
  
  
