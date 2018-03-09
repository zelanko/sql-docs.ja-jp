---
title: "SQL Server のユーザー定義型の登録 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- UDTs [CLR integration], maintaining
- user-defined types [CLR integration], maintaining
- dependencies [CLR integration]
- deploying user-defined types [CLR integration]
- CurrencyConversion function
- user-defined types [CLR integration], deploying
- Transact-SQL deploying UDTs
- assemblies [CLR integration], user-defined types
- cross-database UDT support
- CREATE ASSEMBLY statement
- DROP TYPE statement
- Currency UDT
- CREATE TYPE statement
- registering user-defined types
- UDTs [CLR integration], deploying
- removing user-defined types
- user-defined types [CLR integration], registering
- ALTER ASSEMBLY statement
- UDTs [CLR integration], registering
- ADD FILE clause
ms.assetid: f7da3e92-e407-4f0b-b3a3-f214e442b37d
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 49a0a9d7c9bf8d023b748a34b622ba15e6406233
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="registering-user-defined-types-in-sql-server"></a>SQL Server でのユーザー定義型の登録
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
ユーザー定義型 (UDT) を使用するために[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、登録する必要があります。 UDT を登録するには、UDT を使用するデータベースにアセンブリを登録し、型を作成する必要があります。 UDT は、1 つのデータベースにスコープが設定されるので、同一のアセンブリと UDT を各データベースに登録しない限り、複数のデータベースでは使用できません。 UDT アセンブリを登録し、型を作成すると、[!INCLUDE[tsql](../../includes/tsql-md.md)] やクライアント コードでその UDT を使用できます。 詳細については、「 [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)」を参照してください。  
  
## <a name="using-visual-studio-to-deploy-udts"></a>Visual Studio を使用した UDT の配置  
 UDT を配置する最も簡単な方法は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio を使用することです。 ただし、より複雑な配置シナリオで最も優れた柔軟性を得るためには、このトピックで説明するように [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用します。  
  
 Visual Studio を使用して UDT を作成および配置するには、次の手順を実行します。  
  
1.  新しい**データベース**でプロジェクトを**Visual Basic**または**Visual c#**言語ノード。  
  
2.  UDT を格納する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースへの参照を追加します。  
  
3.  追加、**ユーザー定義型**クラスです。  
  
4.  コードを記述して UDT を実装します。  
  
5.  **ビルド**メニューの **展開**です。 この結果、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースにアセンブリが登録され、型が作成されます。  
  
## <a name="using-transact-sql-to-deploy-udts"></a>Transact-SQL を使用した UDT の配置  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY 構文は、UDT を使用するデータベースにアセンブリを登録する場合に使用します。 アセンブリは、ファイル システムに外部的に格納されるのではなく、データベース システム テーブルに内部的に格納されます。 UDT が外部アセンブリに依存する場合は、それらのアセンブリもデータベースに読み込む必要があります。 CREATE TYPE ステートメントは、UDT を使用するデータベースに UDT を作成する場合に使用します。 詳細については、次を参照してください。 [CREATE ASSEMBLY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-assembly-transact-sql.md)と[型 &#40; を作成します。TRANSACT-SQL と #41 です](../../t-sql/statements/create-type-transact-sql.md)。  
  
### <a name="using-create-assembly"></a>CREATE ASSEMBLY の使用  
 CREATE ASSEMBLY 構文では、UDT を使用するデータベースにアセンブリが登録されます。 アセンブリを登録すると、そのアセンブリに依存関係がなくなります。  
  
 指定された 1 つのデータベースに複数のバージョンの同じアセンブリを作成することはできません。 ただし、特定の 1 つのデータベースに、カルチャに基づいて、複数のバージョンの同じアセンブリを作成することはできます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに登録されているとおりに、異なる名前で、アセンブリの複数のカルチャ バージョンが区別されます。 詳細については、.NET Framework SDK の「厳密な名前付きアセンブリの作成と使用」を参照してください。  
  
 SAFE 権限セットまたは EXTERNAL_ACCESS 権限セットを指定して CREATE ASSEMBLY を実行すると、アセンブリが検証可能でタイプ セーフであることを確認するためのチェックが行われます。 権限セットを指定しないと、SAFE が指定されていると想定されます。 UNSAFE 権限セットを指定したコードはチェックされません。 アセンブリの権限セットの詳細については、次を参照してください。[アセンブリの設計](../../relational-databases/clr-integration/assemblies-designing.md)です。  
  
#### <a name="example"></a>例  
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントに Point アセンブリを登録する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で、 **AdventureWorks** SAFE 権限セットでのデータベースです。 WITH PERMISSION_SET 句を省略すると、SAFE 権限セットでアセンブリが登録されます。  
  
```  
USE AdventureWorks;  
CREATE ASSEMBLY Point  
FROM '\\ShareName\Projects\Point\bin\Point.dll'   
WITH PERMISSION_SET = SAFE;  
```  
  
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントを使用してアセンブリを登録する*< assembly_bits >* FROM 句の引数。 これは、 **varbinary**値がバイト ストリームとして、ファイルを表します。  
  
```  
USE AdventureWorks;  
CREATE ASSEMBLY Point  
FROM 0xfeac4 … 21ac78  
```  
  
### <a name="using-create-type"></a>CREATE TYPE の使用  
 アセンブリをデータベースに読み込むと、[!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE ステートメントを使用して型を作成できます。 型を作成すると、そのデータベースで使用できる型のリストに、作成した型が追加されます。 型にはデータベース スコープがあり、型はその型を作成したデータベースでしか使用できません。 データベース内に UDT が既に存在する場合は、CREATE TYPE ステートメントがエラーで失敗します。  
  
> [!NOTE]  
>  CREATE TYPE 構文は、ネイティブの作成にも使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]別名データ型を置き換えるものでは**sp_addtype**別名データ型を作成するための手段として。 CREATE TYPE 構文の省略可能な一部の引数は CLR の UDT の作成に関係しており、(基本型などの) 別名データ型の作成には適用されません。  
  
 詳細については、次を参照してください。[の種類の作成 &#40;です。TRANSACT-SQL と #41 です](../../t-sql/statements/create-type-transact-sql.md)。  
  
#### <a name="example"></a>例  
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントを作成、**ポイント**型です。 2 部構成の名前付け構文を使用して外部名が指定された*AssemblyName*.*UDTName*です。  
  
```  
CREATE TYPE dbo.Point   
EXTERNAL NAME Point.[Point];  
```  
  
## <a name="removing-a-udt-from-the-database"></a>データベースからの UDT の削除  
 DROP TYPE ステートメントを使用すると、現在のデータベースから UDT が削除されます。 UDT を削除すると、DROP ASSEMBLY ステートメントを使用してデータベースからアセンブリを削除できます。  
  
 DROP TYPE ステートメントは、次の状況では実行されません。  
  
-   UDT を使用して定義した列を含むデータベース内のテーブル。  
  
-   WITH SCHEMABINDING 句を使用してデータベースに作成した UDT の変数またはパラメーターを使用する関数、ストアド プロシージャ、またはトリガー。  
  
### <a name="example"></a>例  
 次の [!INCLUDE[tsql](../../includes/tsql-md.md)] は、この順序どおりに実行する必要があります。 最初、テーブルを参照する、**ポイント**し、型、および最後に、アセンブリ、UDT を削除する必要があります。  
  
```  
DROP TABLE dbo.Points;  
DROP TYPE dbo.Point;  
DROP ASSEMBLY Point;  
```  
  
### <a name="finding-udt-dependencies"></a>UDT 依存関係の検出  
 UDT の列定義を含むテーブルなどの依存オブジェクトがある場合、DROP TYPE ステートメントは失敗します。 また、WITH SCHEMABINDING 句を使用してデータベースに作成した関数、ストアド プロシージャ、またはトリガーがあり、これらのルーチンでユーザー定義型の変数やパラメーターが使用される場合にも失敗します。 最初にすべての依存オブジェクトを削除してから、DROP TYPE ステートメントを実行する必要があります。  
  
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリは、すべての列とで UDT を使用するパラメーターを検索、 **AdventureWorks**データベース。  
  
```  
USE Adventureworks;  
SELECT o.name AS major_name, o.type_desc AS major_type_desc  
     , c.name AS minor_name, c.type_desc AS minor_type_desc  
     , at.assembly_class  
  FROM (  
        SELECT object_id, name, user_type_id, 'SQL_COLUMN' AS type_desc  
          FROM sys.columns  
     UNION ALL  
        SELECT object_id, name, user_type_id, 'SQL_PROCEDURE_PARAMETER'  
          FROM sys.parameters  
     ) AS c  
  JOIN sys.objects AS o  
    ON o.object_id = c.object_id  
  JOIN sys.assembly_types AS at  
    ON at.user_type_id = c.user_type_id;  
```  
  
## <a name="maintaining-udts"></a>UDT の管理  
 UDT を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに作成した後は、型の基になるアセンブリを変更することはできますが、UDT は変更できません。 ほとんどの場合、[!INCLUDE[tsql](../../includes/tsql-md.md)] DROP TYPE ステートメントを使用してデータベースから UDT を削除し、基になるアセンブリに変更を加えて、ALTER ASSEMBLY ステートメントを使用してアセンブリを再読み込みする必要があります。 その後、UDT とすべての依存オブジェクトを再作成する必要があります。  
  
### <a name="example"></a>例  
 ALTER ASSEMBLY ステートメントは、UDT アセンブリのソース コードに変更を加え、ソース コードを再コンパイルした後に使用します。 ALTER ASSEMBLY ステートメントを使用すると、サーバーに .dll ファイルがコピーされ、新しいアセンブリに再バインドされます。 完全な構文を参照してください。 [ALTER ASSEMBLY &#40;です。TRANSACT-SQL と #41 です](../../t-sql/statements/alter-assembly-transact-sql.md)。  
  
 次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY ステートメントでは、ディスク上の指定された場所から Point.dll アセンブリを再読み込みしています。  
  
```  
ALTER ASSEMBLY Point  
FROM '\\Projects\Point\bin\Point.dll'  
```  
  
### <a name="using-alter-assembly-to-add-source-code"></a>ALTER ASSEMBLY を使用したソース コードの追加  
 ALTER ASSEMBLY 構文の ADD FILE 句は、CREATE ASSEMBLY 構文には存在しません。 ADD FILE 句を使用すると、アセンブリに関連付けられるソース コードやその他のファイルを追加できます。 ファイルは元の場所からコピーされ、データベース内のシステム テーブルに格納されます。 これにより、現在のバージョンの UDT を再作成またはドキュメント化する必要があれば、ソース コードや他のファイルをいつでも使用できます。  
  
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]ALTER ASSEMBLY ステートメントの Point.cs クラス ソース コードを追加、**ポイント**UDT です。 Point.cs ファイルに含まれているテキストがコピーされ、"PointSource" という名前でデータベースに格納されます。  
  
```  
ALTER ASSEMBLY Point  
ADD FILE FROM '\\Projects\Point\Point.cs' AS PointSource;  
```  
  
 アセンブリ情報が格納されている、 **sys.assembly_files**アセンブリがインストールされているデータベースのテーブルにします。 **Sys.assembly_files**テーブルには、次の列が含まれています。  
  
 **assembly_id**  
 アセンブリに定義される ID。 この番号は、同じアセンブリに関連するすべてのオブジェクトに割り当てられます。  
  
 **name**  
 オブジェクトの名前。  
  
 **file_id**  
 最初のオブジェクトに関連付けられている各オブジェクトを識別する番号を指定した**assembly_id** 1 の値が指定されています。 同じ関連付けられている複数のオブジェクトがあるかどうか**assembly_id**、その後各**file_id**値が 1 増えます。  
  
 **content**  
 アセンブリまたはファイルの 16 進数表記。  
  
 内容を変換する、CAST または CONVERT 関数を使用することができます、**コンテンツ**を判読できるテキストの列です。 次のクエリでは、結果セットを 1 行に制限するために WHERE 句で name を使用して、Point.cs ファイルの内容を読み取り可能なテキストに変換しています。  
  
```  
SELECT CAST(content AS varchar(8000))   
  FROM sys.assembly_files   
  WHERE name='PointSource';  
```  
  
 結果をテキスト エディターにコピーして貼り付けると、元のファイルに含まれていた改行とスペースが保持されていることがわかります。  
  
## <a name="managing-udts-and-assemblies"></a>UDT とアセンブリの管理  
 UDT の実装を計画するときは、どのメソッドが UDT アセンブリ自体に必要であり、どのメソッドを独立したアセンブリに作成してユーザー定義関数やストアド プロシージャとして実装する必要があるかを検討します。 メソッドを個別のアセンブリに分離すると、テーブルの UDT 列に格納されるデータに影響を与えずに、コードを更新できます。 新しい定義で UDT 列の以前の値を読み取ることができ、型の署名が変更されない場合にのみ、UDT 列や他の依存オブジェクトを削除しないで UDT アセンブリを変更できます。  
  
 UDT の実装に必要なコードから、変更される可能性がある手続き型コードを分離すると、メンテナンスが大幅に簡素化されます。 UDT が機能するのに必要なコードのみを含め、UDT の定義をできる限り単純にしておくと、コード リビジョンやバグ修正のために UDT 自体をデータベースから削除する必要が生じるリスクが軽減されます。  
  
### <a name="the-currency-udt-and-currency-conversion-function"></a>Currency UDT と通貨換算関数  
 **通貨**で UDT、 **AdventureWorks**サンプル データベースは、UDT とその関連機能を構成することをお勧めの役立つ例を提供します。 **通貨**UDT は、特定のカルチャの通貨システムに基づいて金額を処理するために使用でき、ドルやユーロなどのさまざまな通貨型の記憶域。 UDT クラスとして、文字列、および、金額とカルチャ名を公開する、 **decimal**データ型。 必要なシリアル化メソッドは、クラスを定義するアセンブリ内にすべて含まれます。 1 つのカルチャから別の通貨換算を実装している関数はという外部関数として実装**ConvertCurrency**、この関数は、別のアセンブリにあるとします。 **ConvertCurrency**関数内のテーブルから換算率を取得することによって、作業では、 **AdventureWorks**データベース。 換算レートのソースを変更する必要があります、または影響を与えずに、アセンブリを簡単に変更がある場合、既存のコードに何らかの変更場合、**通貨**UDT です。  
  
 コード リストは、**通貨**UDT と**ConvertCurrency**共通言語ランタイム (CLR) サンプルをインストールすることによって機能が見つかりません。  
  
### <a name="using-udts-across-databases"></a>複数のデータベース間での UDT の使用  
 定義上、UDT のスコープは 1 つのデータベースに設定されています。 このため、あるデータベースで定義されている UDT を別のデータベースの列定義に使用することはできません。 UDT を複数のデータベースで使用するには、各データベースで同一のアセンブリに対して CREATE ASSEMBLY ステートメントと CREATE TYPE ステートメントを実行する必要があります。 アセンブリの名前、厳密な名前、カルチャ、バージョン、権限セット、およびバイナリの内容が同じ場合、それらのアセンブリは同一であると見なされます。  
  
 両方のデータベースに UDT を登録し、UDT にアクセスできるようになると、あるデータベースの UDT 値を別のデータベースで使用するために変換できます。 次のシナリオでは、同一の UDT を複数のデータベース間で使用できます。  
  
-   異なるデータベースで定義されているストアド プロシージャの呼び出し。  
  
-   異なるデータベースで定義されているテーブルのクエリ。  
  
-   あるデータベース テーブルの UDT 列から UDT データを選択し、その UDT データを同一の UDT 列を使用して 2 つ目のデータベースに挿入する場合。  
  
 このような状況では、必要なすべての変換がサーバーで自動的に行われます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST 関数または CONVERT 関数を使用して、明示的に変換を実行することはできません。  
  
 Udt を使用するための操作を行う必要はないとき[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]に作業テーブルが作成、 **tempdb**システム データベースです。 これには、テーブル変数、カーソルの処理が含まれます、ユーザー定義テーブル値関数とを含む Udt を透過的にするを使用して**tempdb**です。 ただし、内の一時テーブルを明示的に作成する場合**tempdb** 、UDT 列を定義する、UDT を登録する必要があります**tempdb**ユーザー データベースと同じ方法です。  
  
## <a name="see-also"></a>参照  
 [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
