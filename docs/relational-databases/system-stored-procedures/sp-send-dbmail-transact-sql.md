---
title: "sp_send_dbmail (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sendmail_sp_TSQL
- sendmail_sp
- SP_SEND_DBMAIL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_send_dbmail
ms.assetid: f1d7a795-a3fd-4043-ac4b-c781e76dab47
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7293e16e45c465fa2cfeda2d11888b4dc450d380
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="spsenddbmail-transact-sql"></a>sp_send_dbmail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定した受信者に電子メール メッセージを送信します。 メッセージには、クエリ結果セットまたは添付ファイル、あるいはその両方を含めることができます。 メールが正常にデータベース メール キューに配置しているときに**sp_send_dbmail**を返します、 **mailitem_id**メッセージのです。 このストアド プロシージャは、 **msdb**データベース。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_send_dbmail [ [ @profile_name = ] 'profile_name' ]  
    [ , [ @recipients = ] 'recipients [ ; ...n ]' ]  
    [ , [ @copy_recipients = ] 'copy_recipient [ ; ...n ]' ]  
    [ , [ @blind_copy_recipients = ] 'blind_copy_recipient [ ; ...n ]' ]  
    [ , [ @from_address = ] 'from_address' ]  
    [ , [ @reply_to = ] 'reply_to' ]   
    [ , [ @subject = ] 'subject' ]   
    [ , [ @body = ] 'body' ]   
    [ , [ @body_format = ] 'body_format' ]  
    [ , [ @importance = ] 'importance' ]  
    [ , [ @sensitivity = ] 'sensitivity' ]  
    [ , [ @file_attachments = ] 'attachment [ ; ...n ]' ]  
    [ , [ @query = ] 'query' ]  
    [ , [ @execute_query_database = ] 'execute_query_database' ]  
    [ , [ @attach_query_result_as_file = ] attach_query_result_as_file ]  
    [ , [ @query_attachment_filename = ] query_attachment_filename ]  
    [ , [ @query_result_header = ] query_result_header ]  
    [ , [ @query_result_width = ] query_result_width ]  
    [ , [ @query_result_separator = ] 'query_result_separator' ]  
    [ , [ @exclude_query_output = ] exclude_query_output ]  
    [ , [ @append_query_error = ] append_query_error ]  
    [ , [ @query_no_truncate = ] query_no_truncate ]   
    [ , [ @query_result_no_padding = ] @query_result_no_padding ]   
    [ , [ @mailitem_id = ] mailitem_id ] [ OUTPUT ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@profile_name=** ] **'***profile_name***'**  
 メッセージの送信元プロファイルの名前を指定します。 *Profile_name*の種類は**sysname**、既定値は NULL です。 *Profile_name*既存のデータベース メール プロファイルの名前を指定する必要があります。 ない場合*profile_name*が指定されている**sp_send_dbmail**現在のユーザーの既定のプライベート プロファイルを使用します。 ユーザーが既定のプライベート プロファイルを持たない場合**sp_send_dbmail**の既定のパブリック プロファイルを使用して、 **msdb**データベース。 ユーザーには、既定のプライベート プロファイルはありませんし、データベースの既定のパブリック プロファイルがない場合 **@profile_name** 指定する必要があります。  
  
 [ **@recipients=** ] **'***recipients***'**  
 メッセージの送信先の電子メール アドレスを、セミコロン区切りのリストで指定します。 受信者リストのデータ型**varchar (max)**です。 このパラメーターは省略可能で、少なくとも 1 つの **@recipients** 、  **@copy_recipients** 、または **@blind_copy_recipients** 指定する必要がありますまたは**sp _send_dbmail**はエラーを返します。  
  
 [ **@copy_recipients=** ] **'***copy_recipients***'**  
 メッセージのカーボン コピーを送信する電子メール アドレスを、セミコロン区切りのリストで指定します。 コピーの受信者リストのデータ型**varchar (max)**です。 このパラメーターは省略可能で、少なくとも 1 つの **@recipients** 、  **@copy_recipients** 、または **@blind_copy_recipients** 指定する必要がありますまたは**sp _send_dbmail**はエラーを返します。  
  
 [ **@blind_copy_recipients=** ] **'***blind_copy_recipients***'**  
 メッセージのブラインド カーボン コピーを送信する電子メール アドレスを、セミコロン区切りのリストで指定します。 ブラインド コピーの受信者リストのデータ型**varchar (max)**です。 このパラメーターは省略可能で、少なくとも 1 つの **@recipients** 、  **@copy_recipients** 、または **@blind_copy_recipients** 指定する必要がありますまたは**sp _send_dbmail**はエラーを返します。  
  
 [ **@from_address=** ] **'***from_address***'**  
 電子メール メッセージの差出人アドレスの値を指定します。 これは、メール プロファイルの設定を上書きするためのオプションのパラメーターです。 このパラメーターの型は**varchar (max)**です。 上書きが許可されるかどうかは、SMTP のセキュリティ設定によって決まります。 パラメーターを指定しなかった場合の既定値は NULL です。  
  
 [ **@reply_to=** ] **'***reply_to***'**  
 電子メール メッセージの返信先アドレスの値を指定します。 有効な値として電子メール アドレスが 1 つだけ許可されます。 これは、メール プロファイルの設定を上書きするためのオプションのパラメーターです。 このパラメーターの型は**varchar (max)**です。 上書きが許可されるかどうかは、SMTP のセキュリティ設定によって決まります。 パラメーターを指定しなかった場合の既定値は NULL です。  
  
 [ **@subject=** ] **'***subject***'**  
 電子メール メッセージの件名を指定します。 サブジェクトがの型は**nvarchar (255)**です。 件名を指定しない場合、既定の件名 'SQL Server メッセージ' が使用されます。  
  
 [ **@body=** ] **'***body***'**  
 電子メール メッセージの本文を指定します。 型のメッセージの本文は、 **nvarchar (max)**、既定値は NULL です。  
  
 [ **@body_format=** ] **'***body_format***'**  
 メッセージの本文の形式を指定します。 型のパラメーターが**varchar (20)**、既定値は NULL です。 指定した場合、送信メッセージのヘッダーには、メッセージの本文が指定の形式であることを示す文字列が設定されます。 次のいずれかの値を指定できます。  
  
-   [TEXT]  
  
-   HTML (HTML)  
  
 既定値は TEXT です。  
  
 [ **@importance=** ] **'***importance***'**  
 メッセージの重要度を指定します。 型のパラメーターが**varchar (6)**です。 次のいずれかの値を指定できます。  
  
-   Low  
  
-   標準  
  
-   High  
  
 既定値は Normal です。  
  
 [ **@sensitivity=** ] **'***sensitivity***'**  
 メッセージの秘密度を指定します。 型のパラメーターが**varchar (12)**です。 次のいずれかの値を指定できます。  
  
-   標準  
  
-   Personal  
  
-   Private  
  
-   Confidential  
  
 既定値は Normal です。  
  
 [ **@file_attachments=** ] **'***file_attachments***'**  
 メール メッセージに添付するファイル名を、セミコロン区切りのリストで指定します。 リスト内のファイルは、絶対パスで指定する必要があります。 添付ファイル リストのデータ型**nvarchar (max)**です。 既定では、データベース メールの添付ファイルは 1 ファイルにつき 1 MB に制限されます。  
  
 [ **@query=** ] **'***query***'**  
 実行するクエリを指定します。 クエリの結果をファイルとして添付するか、メッセージの本文に含めるかを指定します。 クエリの種類のデータ**nvarchar (max)**、任意の有効なを含めることができると[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 別のセッション、スクリプトの呼び出しのためのローカル変数に、クエリが実行されたことに注意してください**sp_send_dbmail**はクエリを使用できません。  
  
 [ **@execute_query_database=** ] **'***execute_query_database***'**  
 ストアド プロシージャがクエリを実行するデータベース コンテキストを指定します。 型のパラメーターが**sysname**、現在のデータベースの既定値です。 このパラメーターは、のみ適用場合 **@query** を指定します。  
  
 [ **@attach_query_result_as_file=** ] *attach_query_result_as_file*  
 クエリの結果セットを添付ファイルとして返すかどうかを指定します。 *attach_query_result_as_file*の種類は**ビット**、既定値は 0 です。  
  
 内容の後、クエリの結果が電子メール メッセージの本文に含まれる値が 0 の場合、  **@body** パラメーター。 値が 1 の場合、結果は添付ファイルとして返されます。 このパラメーターは、のみ適用場合 **@query** を指定します。  
  
 [ **@query_attachment_filename=** ] *query_attachment_filename*  
 クエリの結果セットの添付ファイルに使用するファイル名を指定します。 *query_attachment_filename*の種類は**nvarchar (255)**、既定値は NULL です。 このパラメーターは無視されますと*attach_query_result*は 0 です。 ときに*attach_query_result* 1 で、このパラメーターは NULL の場合、データベース メールは、任意のファイル名を作成します。  
  
 [ **@query_result_header=** ] *query_result_header*  
 クエリの結果に列のヘッダーを含めるかどうかを指定します。 Query_result_header 値の型は**ビット**です。 値が 1 の場合、クエリ結果には、列ヘッダーが含まれます。 値が 0 の場合、クエリの結果には列のヘッダーは含まれません。 このパラメーターの既定値**1**です。 このパラメーターは、のみ適用場合 **@query** を指定します。  
  
 [ **@query_result_width** = ] *query_result_width*  
 クエリの結果の書式設定に使用する行の幅を、バイト単位で指定します。 *Query_result_width*の種類は**int**、既定値は 256 です。 値は 10 ～ 32767 の間の数値で指定してください。 このパラメーターは、のみ適用場合 **@query** を指定します。  
  
 [ **@query_result_separator=** ] **'***query_result_separator***'**  
 クエリの出力で列の区切りに使用する文字を指定します。 型の区切り記号は**char (1)**です。 既定値は、' ' (空白文字) です。  
  
 [ **@exclude_query_output=** ] *exclude_query_output*  
 電子メール メッセージ内にクエリ実行の出力を返すかどうかを指定します。 **exclude_query_output**は bit で、既定値は 0 です。 このパラメーターが 0 の場合の実行の場合、 **sp_send_dbmail**ストアド プロシージャは、コンソールで、クエリの実行の結果として返されたメッセージを出力します。 このパラメーターが 1 での実行の場合、 **sp_send_dbmail**ストアド プロシージャが印刷されないクエリの実行のメッセージのいずれかのコンソールにします。  
  
 [ **@append_query_error=** ] *append_query_error*  
 指定されたクエリからエラーが返されるときに電子メールを送信するかどうかを指定します、  **@query** 引数。 **append_query_error**は**ビット**、既定値は 0 です。 このパラメーターの値が 1 の場合、データベース メールでは本文にクエリのエラー メッセージを含めた電子メール メッセージが送信されます。 データベース メールが電子メール メッセージを送信していないこのパラメーターが 0 の場合と**sp_send_dbmail**失敗を示すリターン コード 1、終了します。  
  
 [ **@query_no_truncate=** ] *query_no_truncate*  
 長い可変長データ型の切り捨てを回避するオプションを使用してクエリを実行するかどうかを指定します (**varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、 **xml**、**テキスト**、 **ntext**、**イメージ**、およびユーザー定義データ型)。 設定した場合、クエリの結果には、列ヘッダーが含まれません。 *Query_no_truncate*値の型は**ビット**です。 値が 0 の場合や指定されていない場合、クエリ内の列は 256 文字に切り捨てられます。 値が 1 の場合、クエリ内の列は切り捨てられません。 このパラメーターの既定値は 0 です。  
  
> [!NOTE]  
>  大量のデータで使用する場合、@**query_no_truncate**オプションは、その他のリソースを消費し、サーバーのパフォーマンスが低下することができます。  
  
 [ **@query_result_no_padding** ] *@query_result_no_padding*  
 型は bit です。 既定値は 0 です。 1 に設定すると、クエリ結果埋め込みは行われません、ファイル サイズを小さくする可能性があります。設定した場合@query_result_no_padding1 と設定、@query_result_widthパラメーター、@query_result_no_paddingパラメーターを上書き、@query_result_widthパラメーター。  
  
 この場合、エラーは発生しません。  
  
 設定した場合、 @query_result_no_padding 1 と設定、@query_no_truncateパラメーター、エラーが発生します。  
  
 [ **@mailitem_id=** ] *mailitem_id* [ OUTPUT ]  
 省略可能な出力パラメーターを返します、 *mailitem_id*メッセージのです。 *Mailitem_id*の種類は**int**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 リターン コードが 0 の場合は成功を示します。 その他の値は、エラーを意味します。 失敗したステートメントのエラー コードは、@@ERROR変数。  
  
## <a name="result-sets"></a>結果セット  
 成功すると、"メールがキューに登録されました。" というメッセージが返されます。  
  
## <a name="remarks"></a>解説  
 を使用する前にデータベース メールが可能で、データベース メール構成ウィザードを使用してまたは**sp_configure**です。  
  
 **sysmail_stop_sp**外部プログラムによって使用される Service Broker オブジェクトを停止してデータベース メールを停止します。 **sp_send_dbmail**を使用してデータベース メールが停止したときにメールを受け付ける**sysmail_stop_sp**です。 データベース メールを開始するには使用**sysmail_start_sp**です。  
  
 ときに **@profile** が指定されていない**sp_send_dbmail**既定のプロファイルを使用します。 電子メール メッセージを送信するユーザーに既定のプライベート プロファイルがある場合、データベース メールではそのプロファイルが使用されます。 ユーザーが既定のプライベート プロファイルを持たない場合**sp_send_dbmail**既定パブリック プロファイルを使用します。 ユーザーの既定のプライベート プロファイルと、既定のパブリック プロファイルが存在しない場合**sp_send_dbmail**はエラーを返します。  
  
 **sp_send_dbmail**内容のない電子メール メッセージをサポートしていません。 電子メール メッセージを送信する必要がありますを指定するには、少なくとも 1 つの **@body** 、  **@query** 、  **@file_attachments** 、または **@subject**. それ以外の場合、 **sp_send_dbmail**はエラーを返します。  
  
 データベース メールでは、ファイルへのアクセス制御に現在のユーザーの [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows セキュリティ コンテキストが使用されます。 そのためで認証されるユーザー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証を使用してファイルを添付できません **@file_attachments**です。 Windows では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用してリモート コンピューター間で資格情報を交換することは許可されません。 そのため、データベース メールできないことがあります、コンピューター以外のコンピューターから、コマンドが実行される場合にネットワーク共有からファイルを添付する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上で実行します。  
  
 両方 **@query** と **@file_attachments** 指定されたファイルが見つからないと、クエリがまだ実行しますが、電子メールは送信されません。  
  
 クエリを指定すると、結果セットの書式はインライン テキストに設定されます。 結果セットにあるバイナリ データは 16 進数形式で送信されます。  
  
 パラメーター  **@recipients** 、  **@copy_recipients** 、および **@blind_copy_recipients** の電子メール アドレスのセミコロンで区切られたリストします。 これらのパラメーターの少なくとも 1 つを指定する必要があります、または**sp_send_dbmail**はエラーを返します。  
  
 実行時に**sp_send_dbmail**トランザクションのコンテキストでは、関係なくデータベース メールが開始し、暗黙のトランザクションをコミットします。 実行時に**sp_send_dbmail**から既存のトランザクション内でデータベース メールではユーザーがコミットまたは変更をロールバックします。 内側のトランザクションは開始されません。  
  
## <a name="permissions"></a>権限  
 実行権限**sp_send_dbmail**のすべてのメンバーの既定値は、 **DatabaseMailUser**のデータベース ロール、 **msdb**データベース。 ただし、メッセージを送信するユーザーがいないとき、要求をプロファイルを使用する権限**sp_send_dbmail**エラーが返され、メッセージを送信しません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-sending-an-e-mail-message"></a>A. 電子メール メッセージを送信します。  
 この例では、電子メール メッセージを送信する電子メール アドレスを使用して、友人`myfriend@Adventure-Works.com`です。 メッセージの件名`Automated Success Message`です。 メッセージの本文には、文が含まれています。`'The stored procedure finished successfully'`です。  
  
```  
EXEC msdb.dbo.sp_send_dbmail  
    @profile_name = 'Adventure Works Administrator',  
    @recipients = 'yourfriend@Adventure-Works.com',  
    @body = 'The stored procedure finished successfully.',  
    @subject = 'Automated Success Message' ;  
```  
  
### <a name="b-sending-an-e-mail-message-with-the-results-of-a-query"></a>B. 電子メール メッセージをクエリの結果と共に送信する  
 この例では、電子メール メッセージを送信する電子メール アドレスを使用して、友人`yourfriend@Adventure-Works.com`です。 メッセージの件名は `Work Order Count` で、このメッセージでは `DueDate` が 2004 年 4 月 30 日から 2 日以内となっている作業指示の番号を表示するクエリが実行されます。 データベース メールでは、この結果がテキスト ファイルとして添付されます。  
  
```  
EXEC msdb.dbo.sp_send_dbmail  
    @profile_name = 'Adventure Works Administrator',  
    @recipients = 'yourfriend@Adventure-Works.com',  
    @query = 'SELECT COUNT(*) FROM AdventureWorks2012.Production.WorkOrder  
                  WHERE DueDate > ''2004-04-30''  
                  AND  DATEDIFF(dd, ''2004-04-30'', DueDate) < 2' ,  
    @subject = 'Work Order Count',  
    @attach_query_result_as_file = 1 ;  
```  
  
### <a name="c-sending-an-html-e-mail-message"></a>C. HTML 形式の電子メール メッセージを送信する  
 この例では、電子メール メッセージを送信する電子メール アドレスを使用して、友人`yourfriend@Adventure-Works.com`です。 メッセージの件名`Work Order List`での作業指示を表示する HTML ドキュメントが含まれています、 `DueDate` 2004 年 4 月 30 日から 2 日より小さい。 データベース メールでは、このメッセージが HTML 形式で送信されます。  
  
```  
DECLARE @tableHTML  NVARCHAR(MAX) ;  
  
SET @tableHTML =  
    N'<H1>Work Order Report</H1>' +  
    N'<table border="1">' +  
    N'<tr><th>Work Order ID</th><th>Product ID</th>' +  
    N'<th>Name</th><th>Order Qty</th><th>Due Date</th>' +  
    N'<th>Expected Revenue</th></tr>' +  
    CAST ( ( SELECT td = wo.WorkOrderID,       '',  
                    td = p.ProductID, '',  
                    td = p.Name, '',  
                    td = wo.OrderQty, '',  
                    td = wo.DueDate, '',  
                    td = (p.ListPrice - p.StandardCost) * wo.OrderQty  
              FROM AdventureWorks.Production.WorkOrder as wo  
              JOIN AdventureWorks.Production.Product AS p  
              ON wo.ProductID = p.ProductID  
              WHERE DueDate > '2004-04-30'  
                AND DATEDIFF(dd, '2004-04-30', DueDate) < 2   
              ORDER BY DueDate ASC,  
                       (p.ListPrice - p.StandardCost) * wo.OrderQty DESC  
              FOR XML PATH('tr'), TYPE   
    ) AS NVARCHAR(MAX) ) +  
    N'</table>' ;  
  
EXEC msdb.dbo.sp_send_dbmail @recipients='yourfriend@Adventure-Works.com',  
    @subject = 'Work Order List',  
    @body = @tableHTML,  
    @body_format = 'HTML' ;  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール構成オブジェクト](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [データベース メールのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)  
  
  
