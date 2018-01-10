---
title: "TRANSACT-SQL 構文表記規則 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: sql13.TSQLExpandPortal.f1
dev_langs: TSQL
helpviewer_keywords:
- conventions [SQL Server]
- Applies to section in Transact-SQL topics
- code example conventions [SQL Server]
- objects [SQL Server], names
- code [SQL Server], conventions
- multipart names [SQL Server]
- Transact-SQL syntax conventions
- syntax conventions [SQL Server]
- code [SQL Server]
- Transact-SQL
- naming conventions [SQL Server]
- syntax [SQL Server], Transact-SQL
ms.assetid: 35fbcf7f-8b55-46cd-a957-9b8c7b311241
caps.latest.revision: "55"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: dfc99736884d458bdbce890bfcc4f80185115b29
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="transact-sql-syntax-conventions-transact-sql"></a>Transact-SQL 構文表記規則 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  次の表は、[!INCLUDE[tsql](../../includes/tsql-md.md)] リファレンスの構文で使用している表記規則について示しています。  
  
|表記|使用目的|  
|----------------|--------------|  
|大文字|[!INCLUDE[tsql](../../includes/tsql-md.md)] キーワードを示します。|  
|*斜体*|ユーザーが指定する [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文のパラメーターを示します。|  
|**太字**|記載されているとおりに入力する必要があるデータベース名、テーブル名、列名、インデックス名、ストアド プロシージャ、ユーティリティ、データ型名、テキストを示します。|  
|**下線**|下線が引かれている値を含む句がステートメントから省略されているときに適用される既定値を示します。|  
|(& a) #124 です。(縦棒)|角かっこ、または中かっこで囲まれた構文項目を区切ります。 使用できる項目は 1 つだけです。|  
|`[ ]` (角かっこ)|省略可能な構文項目。 角かっこは入力しません。|  
|{} (中かっこ)|必須の構文項目を示します。 中かっこは入力しません。|  
|[**,**...*n*]|先行する項目が繰り返せることを示します *n* 回数。 項目はコンマで区切ります。|  
|[...*n*]|先行する項目が繰り返せることを示します *n* 回数。 項目は空白で区切ります。|  
|;|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのターミネータを示します。セミコロンは、このバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のほとんどのステートメントでは必須ではありませんが、将来のバージョンでは必須となる予定です。|  
|\<ラベル >:: =|構文のブロックの名前を示します。 この表記規則は、1 つのステートメント内の複数の箇所で使用できる長い構文の一部、または構文の 1 単位について、グループ化してラベルを付ける際に使用します。 構文のブロックを使用できる箇所は山かっこで囲まれたラベル:\<ラベル >。<br /><br /> セットは、式のコレクションがたとえば\<セットをグループ化 >; 一覧は、セットのコレクションなどと\<複合要素一覧 >。|  
  
## <a name="multipart-names"></a>マルチパート名  
 特に指定のない限り、データベース オブジェクトの名前に対するすべての [!INCLUDE[tsql](../../includes/tsql-md.md)] 参照は、次のような 4 部構成の名前の形式をとります。  
  
 *server_name* **.**[*database_name*]**.**[*schema_name*]**.***object_name*  
  
 | *database_name***.**[*schema_name*]**.***object_name*  
  
 | *schema_name***.***object_name*  
  
 *|object_name*  
  
 *サーバー名*  
 リンク サーバー名またはリモート サーバー名を示します。  
  
 *database_name*  
 オブジェクトが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスに存在するときは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースの名前を指定します。 オブジェクトは、リンク サーバーが*database_name* OLE DB カタログを指定します。  
  
 *schema_name*  
 オブジェクトを含む場合は、オブジェクトがスキーマの名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。 オブジェクトは、リンク サーバーが*schema_name* OLE DB スキーマ名を指定します。  
  
 *object_name*  
 オブジェクトの名前を示します。  
  
 特定のオブジェクトを参照するときに常がありませんサーバー、データベース、およびスキーマを指定する、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]オブジェクトを識別します。 ただし、オブジェクトが見つからない場合、エラーが返されます。  
  
> [!NOTE]  
>  名前解決のエラーを回避するために、スキーマ スコープ オブジェクトを指定するときは、常にスキーマ名を指定することをお勧めします。  
  
 中間のノードを省略するには、ピリオドを使用してそれらの位置を示します。 次の表に、オブジェクト名の有効な形式を示します。  
  
|オブジェクト参照形式|Description|  
|-----------------------------|-----------------|  
|*サーバー* **です。** *データベース***です。** *スキーマ***です。** *オブジェクト*|4 部構成の名前です。|  
|*サーバー* **です。** *データベース* **.** *オブジェクト*|スキーマ名を省略しています。|  
|*サーバー* **.** *スキーマ***です。** *オブジェクト*|データベース名を省略しています。|  
|*サーバー* **しています.** *オブジェクト*|データベースとスキーマ名を省略しています。|  
|*データベース***です。** *スキーマ***です。** *オブジェクト*|サーバー名を省略しています。|  
|*データベース* **.** *オブジェクト*|サーバーとスキーマ名を省略しています。|  
|*スキーマ***です。** *オブジェクト*|サーバーとデータベース名を省略しています。|  
|*オブジェクト*|サーバー、データベース、およびスキーマ名を省略しています。|  
  
## <a name="code-example-conventions"></a>コード例の規則  
 提供される例をそれ以外の場合、特に記されていない、[!INCLUDE[tsql](../../includes/tsql-md.md)]参照を使用して、テストされた[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]と、次のオプションの既定の設定。  
  
-   ANSI_NULLS  
  
-   ANSI_NULL_DFLT_ON  
  
-   ANSI_PADDING  
  
-   ANSI_WARNINGS  
  
-   CONCAT_NULL_YIELDS_NULL  
  
-   QUOTED_IDENTIFIER  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] リファレンスのほとんどのコード例は、大文字と小文字を区別する並べ替え順を使用するサーバーでテストされています。 通常、テスト サーバーでは、ANSI/ISO 1252 コード ページが使用されています。  
  
 多くのコード例は、文字で Unicode 文字列定数をプレフィックス**N**です。なし、 **N**プレフィックスは、文字列は、データベースの既定のコード ページに変換されます。 この既定のコード ページでは、一部の文字が認識されない場合があります。  
  
## <a name="applies-to-references"></a>"適用対象" リファレンス  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]リファレンスに関連する記事の内容は[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、および[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]です。 各記事の上部にある、記事の主題をサポートする製品を示すセクションです。 製品を省略すると、この記事で説明されている機能はその製品で使用できません。 たとえば、可用性グループで導入された[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]です。 **CREATE AVAILABILITY GROUP**記事に適用されることを示します**SQL Server (SQL Server 2012 ~ 現行バージョン)**には適用されないため[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、または[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 場合によっては、アーティクルの一般的な主題は製品で使用できますが、すべての引数はサポートされていません。 たとえば、包含データベース ユーザーは [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] で導入されました。 **CREATE USER**ステートメントは、いずれかで使用できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]製品、ただし、 **WITH PASSWORD**構文は、以前のバージョンでは使用できません。 この場合、追加で**対象**セクションの記事の本文に適切な引数の説明に挿入されます。  
  
## <a name="see-also"></a>参照  
 [TRANSACT-SQL リファレンス &#40;データベース エンジン&#41;](../../t-sql/transact-sql-reference-database-engine.md)  
  
  


