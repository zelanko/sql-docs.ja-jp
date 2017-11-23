---
title: "ALTER DATABASE (並列データ ウェアハウス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5751656b-7aae-4152-a314-4c631bea4fc4
caps.latest.revision: "10"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 522f8c8404e80943e093ebeb0a56698fa790b6c9
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="alter-database-parallel-data-warehouse"></a>ALTER DATABASE (並列データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  レプリケートされたテーブル、分散テーブル、および内のトランザクション ログの最大データベース サイズのオプションを変更[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。 このステートメントを使用すると、それを拡大または縮小のサイズとデータベースのディスク領域の割り当てを管理できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Parallel Data Warehouse  
ALTER DATABASE database_name    
    SET ( <set_database_options>   | <db_encryption_option> )  
[;]  
  
<set_database_options> ::=   
{  
    AUTOGROW = { ON | OFF }  
    | REPLICATED_SIZE = size [GB]  
    | DISTRIBUTED_SIZE = size [GB]  
    | LOG_SIZE = size [GB]  
}  
  
<db_encryption_option> ::=  
    ENCRYPTION { ON | OFF }  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 変更するデータベースの名前。 アプライアンス上のデータベースの一覧を表示する使用[sys.databases &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
 自動拡張 = {ON |オフ}  
 自動拡張オプションを更新します。 自動拡張が ON の場合、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]記憶域の要件の増大に対応するために必要とレプリケートされたテーブル、分散テーブル、およびトランザクション ログに割り当てられた領域を自動的に増加します。 自動拡張が OFF の場合、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]エラーを返します、テーブルをレプリケートされた場合に分散テーブル、またはトランザクション ログが最大サイズの設定を超えています。  
  
 REPLICATED_SIZE =*サイズ*[GB]  
 変更されているデータベース内のすべてのレプリケートされたテーブルを格納するためのコンピューティング ノードごとの新しい最大ギガバイト単位を指定します。 アプライアンスの記憶域スペースを計画している場合は、アプライアンスにコンピューティング ノードの数によって REPLICATED_SIZE を乗算する必要があります。  
  
 DISTRIBUTED_SIZE =*サイズ*[GB]  
 変更されているデータベース内のすべての分散テーブルを格納するためのデータベースあたり最大ギガバイト単位の新しいを指定します。 サイズは、すべてのアプライアンスにコンピューティング ノードに分散されます。  
  
 LOG_SIZE =*サイズ*[GB]  
 変更されているデータベース内のすべてのトランザクション ログを格納するためのデータベースあたり最大ギガバイト単位の新しいを指定します。 サイズは、すべてのアプライアンスにコンピューティング ノードに分散されます。  
  
 暗号化 {ON |オフ}  
 データベースを暗号化する (ON) か、暗号化しない (OFF) かを設定します。 暗号化のみに対して設定できる[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]とき[sp_pdw_database_encryption](http://msdn.microsoft.com/5011bb7b-1793-4b2b-bd9c-d4a8c8626b6e)に設定されている**1**です。 透過的なデータ暗号化を構成する前に、データベース暗号化キーを作成する必要があります。 データベース暗号化の詳細については、次を参照してください。 [Transparent Data Encryption &#40;です。TDE &#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
## <a name="permissions"></a>Permissions  
 データベースに対する ALTER 権限が必要です。  
  
## <a name="general-remarks"></a>全般的な解説  
 REPLICATED_SIZE、DISTRIBUTED_SIZE、LOG_SIZE の値より大きい、同じか、またはデータベースの現在の値よりも小さいかを使用できます。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 拡張し、圧縮操作はおおよそのものです。 結果として得られる実際のサイズは、サイズのパラメーターによって異なります。  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]分割不可能な操作として、ALTER DATABASE ステートメントは実行されません。 ステートメントが実行中に中止されると、既に発生した変更は残ります。  
  
## <a name="locking-behavior"></a>ロック動作  
 データベース オブジェクトの共有ロックを取得します。 読み取りまたは書き込み用に別のユーザーが使用されているデータベースを変更することはできません。 これには、発行したセッションが含まれます、[使用](http://msdn.microsoft.com/158ec56b-b822-410f-a7c4-1a196d4f0e15)データベース上のステートメント。  
  
## <a name="performance"></a>パフォーマンス  
 データベースを圧縮すると、大量のデータベース内の実際のデータのサイズによっては、時間とシステムのリソースとディスクの断片化の量が実行できます。 たとえば、データベースの圧縮かかる場合があります数時間またはそれ以上です。  
  
## <a name="determining-encryption-progress"></a>暗号化の進行状況を判断します。  
 割合で示したデータベース透過的なデータ暗号化の進行状況を判断するのにには、次のクエリを使用します。  
  
```  
WITH  
database_dek AS (  
    SELECT ISNULL(db_map.database_id, dek.database_id) AS database_id,  
        dek.encryption_state, dek.percent_complete,  
        dek.key_algorithm, dek.key_length, dek.encryptor_thumbprint,  
        type  
    FROM sys.dm_pdw_nodes_database_encryption_keys AS dek  
    INNER JOIN sys.pdw_nodes_pdw_physical_databases AS node_db_map  
        ON dek.database_id = node_db_map.database_id   
        AND dek.pdw_node_id = node_db_map.pdw_node_id  
    LEFT JOIN sys.pdw_database_mappings AS db_map  
        ON node_db_map .physical_name = db_map.physical_name  
    INNER JOIN sys.dm_pdw_nodes nodes  
        ON nodes.pdw_node_id = dek.pdw_node_id  
    WHERE dek.encryptor_thumbprint <> 0x  
),  
dek_percent_complete AS (  
    SELECT database_dek.database_id, AVG(database_dek.percent_complete) AS percent_complete  
    FROM database_dek  
    WHERE type = 'COMPUTE'  
    GROUP BY database_dek.database_id  
)  
SELECT DB_NAME( database_dek.database_id ) AS name,  
    database_dek.database_id,  
    ISNULL(  
       (SELECT TOP 1 dek_encryption_state.encryption_state  
        FROM database_dek AS dek_encryption_state  
        WHERE dek_encryption_state.database_id = database_dek.database_id  
        ORDER BY (CASE encryption_state  
            WHEN 3 THEN -1  
            ELSE encryption_state  
            END) DESC), 0)  
        AS encryption_state,  
dek_percent_complete.percent_complete,  
database_dek.key_algorithm, database_dek.key_length, database_dek.encryptor_thumbprint  
FROM database_dek  
INNER JOIN dek_percent_complete   
    ON dek_percent_complete.database_id = database_dek.database_id  
WHERE type = 'CONTROL';  
```  
  
 TDE を実装するすべての手順を示す包括的な例を参照してください。 [Transparent Data Encryption &#40;です。TDE &#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-altering-the-autogrow-setting"></a>A. 自動拡張の設定を変更します。  
 データベースの自動拡張を ON に設定`CustomerSales`です。  
  
```  
ALTER DATABASE CustomerSales  
    SET ( AUTOGROW = ON );  
```  
  
### <a name="b-altering-the-maximum-storage-for-replicated-tables"></a>B. レプリケートされたテーブルの最大記憶域を変更します。  
 次の例は、データベースの 1 GB にレプリケートされたテーブル記憶域の上限を設定`CustomerSales`です。 これは、コンピューティング ノードごとの記憶域の上限です。  
  
```  
ALTER DATABASE CustomerSales  
    SET ( REPLICATED_SIZE = 1 GB );  
```  
  
### <a name="c-altering-the-maximum-storage-for-distributed-tables"></a>C. 分散テーブルの最大記憶域を変更します。  
 次の例では、1000 GB (1 テラバイト) を分散テーブル記憶域の上限を設定、データベースの`CustomerSales`します。 これは、コンピューティング ノードごとの記憶域制限しないすべてのコンピューティング ノードのアプライアンスにわたって結合された記憶域の上限です。  
  
```  
ALTER DATABASE CustomerSales  
    SET ( DISTRIBUTED_SIZE = 1000 GB );  
```  
  
### <a name="d-altering-the-maximum-storage-for-the-transaction-log"></a>D. トランザクション ログの最大記憶域を変更します。  
 次の例は、データベースを更新`CustomerSales`する最大持つ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アプライアンスの 10 gb のトランザクション ログのサイズ。  
  
```  
ALTER DATABASE CustomerSales  
    SET ( LOG_SIZE = 10 GB );  
```  
  
## <a name="see-also"></a>参照  
 [DATABASE &#40; を作成します。並列データ ウェアハウス&#41;](../../t-sql/statements/create-database-parallel-data-warehouse.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)  
  
  
