---
title: "リモート テーブルとして選択 (並列データ ウェアハウス) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.service: sql-data-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16ef8191-7587-45a3-9ee9-7d99b7088de3
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a0318d108d6dfaaa374af9a1ab8a148ff960dfcd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-remote-table-as-select-parallel-data-warehouse"></a>リモート テーブルとして選択 (並列データ ウェアハウス) を作成します。
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  データを選択、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]データベースにあり、SMP で新しいテーブルにそのデータをコピー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]リモート サーバー上のデータベースです。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]MPP クエリのリモート コピーのデータを選択する、処理のすべての利点とアプライアンスを使用します。 このシナリオを使用を必要とする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]機能します。  
  
 リモート サーバーを構成するのには「リモート テーブルのコピー」を参照してください、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE REMOTE TABLE [ database_name . [ schema_name ] . | schema_name. ] table_name     AT ('<connection_string>')  
    [ WITH ( BATCH_SIZE = batch_size ) ]  
    AS <select_statement>  
[;]  
  
<connection_string> ::=   
    Data Source = { IP_address | hostname } [, port ]; User ID = user_name ;Password = password;  
  
<select_statement> ::=  
    [ WITH <common_table_expression> [ ,...n ] ]  
    SELECT <select_criteria>  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 リモート テーブルを作成するデータベースです。 *database_name*は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。 既定値は、先にユーザーのログインの既定のデータベース[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。  
  
 *schema_name*  
 新しいテーブルのスキーマです。 既定値は、先にユーザーのログインの既定のスキーマ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。  
  
 *table_name*  
 新しいテーブルの名前です。 詳細についてはテーブル名を許可されているで「オブジェクトの名前付け規則」を参照してください、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。  
  
 リモート テーブルがヒープとして作成されます。 Check 制約やトリガーはありません。 リモート テーブルの列の照合順序は、ソース テーブルの列の照合順序と同じです。 これは型の列に当てはまります**char**、 **nchar**、 **varchar**、および**nvarchar**です。  
  
 *connection_string*  
 文字の文字列を指定する、 `Data Source`、 `User ID`、および`Password`リモート サーバーとデータベースに接続するためのパラメーターです。  
  
 接続文字列は、キーと値のペアのセミコロンで区切られた一覧です。 キーワードは、大文字小文字が区別されません。 キーと値のペア間のスペースは無視されます。 ただし、値は、データ ソースによっては、大文字小文字が区別にあります。  
  
 *[データ ソース]*  
 リモートの SMP のポート番号を名前または IP アドレスと TCP を指定するパラメーター[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 *ホスト名*または*IP_address*  
 リモート サーバー コンピューターまたはリモート サーバーの IPv4 アドレスの名前。 IPv6 アドレスはサポートされていません。 指定することができます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]名前付きインスタンスの形式で**Computer_Name\Instance_Name**または**IP_address\Instance_Name**です。 サーバーは、リモートである必要があり、(local) として指定することはできません。  
  
 TCP*ポート*数  
 接続の TCP ポート番号。 既定のポート 1433 でリッスンしていない SQL Server のインスタンスの 0 から 65535 までの TCP ポート番号を指定できます。 例: **ServerA 1450**または**10.192.14.27,1435**  
  
> [!NOTE]  
>  IP アドレスを使用してリモート サーバーに接続することをお勧めします。 構成によっては、ネットワーク、コンピューター名を使用して接続する、正しいサーバーに名前を解決するのには、非アプライアンスの DNS サーバーを使用する追加の手順が必要があります。 IP アドレスに接続するときに、この手順は必要ではありません。 詳細についてを参照してください「を解決する非アプライアンスの DNS 名 (Analytics Platform System) に、DNS フォワーダーを使用して」、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。  
  
 *user_name*  
 有効な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証ログイン名。 最大文字数は 128 です。  
  
 *パスワード*  
 ログイン パスワード。 最大文字数は 128 です。  
  
 *batch_size*  
 バッチごとの行数の最大数。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]行をバッチで移行先サーバーに送信します。 *Batch_size*正の整数 > = 0。 既定値は 0 です。  
  
 *Common_table_expression*  
 共通テーブル式 (CTE) と呼ばれる一時的な名前付き結果セットを指定します。 詳細については、次を参照してください。[で common_table_expression と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 選択\<select_criteria > 新しいリモート テーブルを構成するデータを指定するクエリ述語です。 詳細については、SELECT ステートメントは、次を参照してください[SELECT &#40;。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 必要です。  
  
-   SELECT 句内の各オブジェクトのアクセス許可を選択します。  
  
-   移行先 SMP データベースに対する CREATE TABLE 権限が必要です。  
  
-   ALTER、INSERT、および送信先 SMP スキーマに対する SELECT 権限が必要です。  
  
## <a name="error-handling"></a>エラー処理  
 リモート データベースへのデータのコピーに失敗した場合[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]操作を中止、エラー ログに記録され、リモート テーブルを削除しようとしています。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]新しいテーブルのクリーンアップは保証されません。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 **移行先のリモート サーバー**:  
  
-   TCP は、既定値は、およびプロトコルをリモート サーバーへの接続でのみサポートします。  
  
-   移行先サーバーは、非アプライアンス サーバーである必要があります。 CREATE REMOTE TABLE は、1 つのアプライアンス間でデータをコピーするには使用できません。  
  
-   CREATE REMOTE TABLE ステートメントには、新しいテーブルのみを作成します。 したがって、新しいテーブルは既に存在できません。 リモート データベースとスキーマが既に存在する必要があります。  
  
-   リモート サーバーは、アプライアンスから転送されるデータの格納に使用可能な領域を持つ必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]リモート データベース。  
  
 **SELECT ステートメント**:  
  
-   選択条件では、ORDER BY および TOP 句はサポートされていません。  
  
-   アクティブなトランザクション内部、または自動コミット オフ設定では、セッションがアクティブなときに、CREATE REMOTE TABLE を実行できません。  
  
 [SET ROWCOUNT と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-rowcount-transact-sql.md)このステートメントでも何も起こりません。 同様の動作を実現するために使用[TOP & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/top-transact-sql.md).  
  
## <a name="locking-behavior"></a>ロック動作  
 リモート テーブルを作成した後、コピーを開始するまで、変換先テーブルをロックしません。 したがって、別のプロセスを作成した後、およびコピーを開始する前に、リモート テーブルを削除することができます。 この場合、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]でエラーが発生し、コピーは失敗します。  
  
## <a name="metadata"></a>メタデータ  
 使用して[sys.dm_pdw_dms_workers & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md)リモート SMP サーバーへの選択したデータのコピーの進行状況を表示します。 PARALLEL_COPY_READER の種類を持つ行には、この情報が含まれています。  
  
## <a name="security"></a>セキュリティ  
 CREATE REMOTE TABLE を使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]リモートへの接続に認証[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスです。 Windows 認証は使用されません。  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]の例外が、外部に公開されたネットワークをファイアウォール必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ポート、管理ポート、および管理のポートです。  
  
 偶発的なデータの消失または破損を防ぐために、アプライアンスから転送先データベースにコピーするために使用するユーザー アカウントが、転送先データベースにのみ、最低限必要なアクセス許可が必要です。  
  
 接続設定では、SMP に接続できます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザー名とパスワードのデータを保護する SSL ではなく、実際のデータがクリア テキストで暗号化されずに送信されているインスタンス。 この場合、悪意のあるユーザーが CREATE REMOTE TABLE ステートメントのテキストが含まれてをインターセプトでした、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SMP にログオンするユーザー名とパスワード[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。 このリスクを避けるためには、SMP への接続でデータの暗号化を使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。  
  
##  <a name="Examples"></a> 使用例  
  
### <a name="a-creating-a-remote-table"></a>A. リモート テーブルを作成します。  
 この例で作成、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SMP のリモート テーブルと呼ばれる`MyOrdersTable`データベースで`OrderReporting`とスキーマ`Orders`です。 `OrderReporting`という名前のサーバーにあるデータベース`SQLA`を既定のポート 1433 をリッスンします。 サーバーへの接続がユーザーの資格情報を使用して`David`、パスワードの`e4n8@3`します。  
  
```  
CREATE REMOTE TABLE OrderReporting.Orders.MyOrdersTable  
AT ( 'Data Source = SQLA, 1433; User ID = David; Password = e4n8@3;' )  
AS SELECT <select_criteria>;  
```  
  
### <a name="b-querying-the-sysdmpdwdmsworkers-dmv-for-remote-table-copy-status"></a>B. リモート テーブルのコピーのステータスの sys.dm_pdw_dms_workers DMV のクエリを実行します。  
 このクエリは、リモート テーブルのコピーのコピー状態を表示する方法を示します。  
  
```  
SELECT * FROM sys.dm_pdw_dms_workers   
WHERE type = 'PARALLEL_COPY_READER';  
```  
  
### <a name="c-using-a-query-join-hint-with-create-remote-table"></a>C. リモート テーブルの作成とクエリの結合ヒントを使用します。  
 このクエリは、リモート テーブルの作成とクエリの結合ヒントを使用するための基本構文を示しています。 クエリは、コントロール ノードに送信された後[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、コンピューティング ノードで実行されている、生成するときに、ハッシュ結合の方法を適用、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クエリ プラン。 結合ヒントや、OPTION 句を使用する方法の詳細については、次を参照してください。 [OPTION 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/option-clause-transact-sql.md).  
  
```  
USE ssawPDW;  
CREATE REMOTE TABLE OrderReporting.Orders.MyOrdersTable  
AT ( 'Data Source = SQLA, 1433; User ID = David; Password = e4n8@3;' )  
    AS SELECT T1.* FROM OrderReporting.Orders.MyOrdersTable T1   
    JOIN OrderReporting.Order.Customer T2  
    ON T1.CustomerID=T2.CustomerID OPTION (HASH JOIN);  
```  
  
  


