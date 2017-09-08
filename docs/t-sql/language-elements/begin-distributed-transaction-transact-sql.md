---
title: "分散トランザクション (TRANSACT-SQL) を開始 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/29/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DISTRIBUTED
- BEGIN_DISTRIBUTED_TRANSACTION_TSQL
- DISTRIBUTED_TSQL
- BEGIN DISTRIBUTED TRANSACTION
dev_langs:
- TSQL
helpviewer_keywords:
- BEGIN DISTRIBUTED TRANSACTION statement
- distributed transactions [SQL Server], starting
- MS DTC, transaction management
- distributed transactions [SQL Server], BEGIN DISTRIBUTED TRANSACTION statement
- servers [SQL Server], distributed transactions
- starting distributed transactions
- remote servers [SQL Server], distributed transactions
- starting transactions
ms.assetid: c3bc2716-39d3-4061-8c6a-8734899231ac
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 93287230933c8ad33bc72185b2b26402ef8048fa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="begin-distributed-transaction-transact-sql"></a>BEGIN DISTRIBUTED TRANSACTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  開始を指定、[!INCLUDE[tsql](../../includes/tsql-md.md)]分散トランザクションによって管理される[!INCLUDE[msCoName](../../includes/msconame-md.md)]分散トランザクション コーディネーター (MS DTC)。  
    
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
BEGIN DISTRIBUTED { TRAN | TRANSACTION }   
     [ transaction_name | @tran_name_variable ]   
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *では無視*  
 MS DTC ユーティリティ内で分散管理トランザクションの追跡に使用する、ユーザー定義のトランザクション名を指定します。 *では無視*識別子の規則に従う必要がありする必要があります\<= 32 文字です。  
  
 @*tran_name_variable*  
 MS DTC ユーティリティ内で分散管理トランザクションの追跡に使用するトランザクション名を含む、ユーザー定義の変数名を指定します。 変数を宣言する必要があります、 **char**、 **varchar**、 **nchar**、または**nvarchar**データ型。  
  
## <a name="remarks"></a>解説  
 BEGIN DISTRIBUTED TRANSACTION ステートメントを実行する [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] インスタンスは、トランザクションの発行元となり、トランザクションの完了を制御します。 このセッションで後続の COMMIT TRANSACTION または ROLLBACK TRANSACTION ステートメントを実行すると、制御側のインスタンスから MS DTC に対して、関係する全インスタンス間の分散トランザクションの完了を管理するように要求されます。  
  
 トランザクション レベルのスナップショット分離では、分散トランザクションはサポートされません。  
  
 主な方法のリモート インスタンス、[!INCLUDE[ssDE](../../includes/ssde-md.md)]に参加している分散トランザクションは分散トランザクションに既に参加しているセッションは、リンク サーバーを参照する分散クエリを実行するとします。  
  
 たとえば、BEGIN DISTRIBUTED TRANSACTION が ServerA で実行されると、そのセッションでは ServerB のストアド プロシージャと ServerC のストアド プロシージャが呼び出されます。 ServerC のストアド プロシージャでは ServerD に対して分散クエリが実行され、この結果、4 台のコンピューターすべてが分散トランザクションに参加します。 ServerA の[!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスは、トランザクションの発行元の制御インスタンスになります。  
  
 いるセッションで[!INCLUDE[tsql](../../includes/tsql-md.md)]分散トランザクションは分散トランザクションに明示的に参加させるのには、別のセッションに渡すことができますが、トランザクション オブジェクトを取得できません。 リモート サーバーがトランザクションに参加できるのは、リモート サーバーが分散クエリまたはリモート ストアド プロシージャ コールの対象になる場合だけです。  
  
 分散クエリが実行すると、ローカル トランザクション内ターゲット OLE DB データ ソースは、ITransactionLocal をサポートしている場合、トランザクションが分散トランザクションに自動的に昇格します。 ターゲットの OLE DB データ ソースが ITransactionLocal をサポートしていない場合、分散クエリでは読み取り専用操作だけが許可されています。  
  
 分散トランザクションに既に参加しているセッションでは、リモート サーバーを参照するリモート ストアド プロシージャが実行されます。  
  
 **Sp_configure リモート proc trans**オプションでは、ローカル トランザクション内のリモート ストアド プロシージャを呼び出す MS DTC によって管理される分散トランザクションに昇格するローカル トランザクションが自動的に発生するかどうかを制御します。 接続レベルの SET オプション REMOTE_PROC_TRANSACTIONS は、によって確立されたインスタンスの既定値をオーバーライドするために使用できる**sp_configure リモート proc trans**です。このオプションをオンに設定した状態でリモート ストアド プロシージャを呼び出すと、ローカル トランザクションは分散トランザクションに昇格します。 この場合、MS DTC トランザクションを作成した接続がトランザクションの発行元になります。 COMMIT TRANSACTION では、MS DTC により調整されるコミットが開始されます。 場合、 **sp_configure リモート proc trans**オプションが ON に、ローカル トランザクションでのリモート ストアド プロシージャ呼び出しが分散トランザクションの一部として具体的には問題をアプリケーションを書き直しをせずに自動的に保護されました。BEGIN DISTRIBUTED TRANSACTION BEGIN TRANSACTION の代わりにします。  
  
 分散トランザクションの環境と処理の詳細については、[!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーターのマニュアルを参照してください。  
  
## <a name="permissions"></a>Permissions  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 この例から候補者を削除する、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]の両方のローカル インスタンス上のデータベース、[!INCLUDE[ssDE](../../includes/ssde-md.md)]とリモート サーバー上のインスタンス。 ローカルとリモートの両方のデータベースで、トランザクションのコミットまたはロールバックのいずれかが実行されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスが動作しているコンピューターに現在 MS DTC がインストールされていない場合、この例を実行するとエラー メッセージが出力されます。 MS DTC のインストールの詳細については、Microsoft 分散トランザクション コーディネーターのマニュアルを参照してください。  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN DISTRIBUTED TRANSACTION;  
-- Delete candidate from local instance.  
DELETE AdventureWorks2012.HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
-- Delete candidate from remote instance.  
DELETE RemoteServer.AdventureWorks2012.HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
COMMIT TRANSACTION;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [BEGIN TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [COMMIT TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [コミット動作 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [ROLLBACK WORK & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/rollback-work-transact-sql.md)   
 [SAVE TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/save-transaction-transact-sql.md)  
  
  

