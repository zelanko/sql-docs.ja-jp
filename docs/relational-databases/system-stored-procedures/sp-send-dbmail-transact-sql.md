---
title: sp_send_dbmail (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52a89c0220bddde6944e759936dc22ad1f3e0ff2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68126303"
---
# <a name="spsenddbmail-transact-sql"></a>sp_send_dbmail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定した受信者に電子メール メッセージを送信します。 メッセージには、クエリの結果セット、添付ファイル、またはその両方を含めることができます。 メールが正常にデータベース メール キューに配置されるときに**sp_send_dbmail**を返します、 **mailitem_id**メッセージ。 このストアド プロシージャは、 **msdb**データベース。  
  
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
`[ @profile_name = ] 'profile_name'` メッセージを送信するプロファイルの名前です。 *Profile_name*の種類は**sysname**、既定値は NULL です。 *Profile_name*既存のデータベース メール プロファイルの名前を指定する必要があります。 ない場合*profile_name*が指定されている**sp_send_dbmail**現在のユーザーの既定のプライベート プロファイルを使用します。 ユーザーが既定のプライベート プロファイルを持たない場合**sp_send_dbmail**の既定のパブリック プロファイルを使用して、 **msdb**データベース。 ユーザーに既定のプライベート プロファイルがないし、データベースの既定のパブリック プロファイルがない場合 **@profile_name** 指定する必要があります。  
  
`[ @recipients = ] 'recipients'` メッセージを送信する電子メール アドレスのセミコロン区切りの一覧を示します。 受信者リストのデータ型**varchar (max)** します。 このパラメーターは省略可能な少なくとも 1 つの **@recipients** 、 **@copy_recipients** 、または **@blind_copy_recipients** 指定する必要がありますまたは**sp _send_dbmail**はエラーを返します。  
  
`[ @copy_recipients = ] 'copy_recipients'` メッセージをアドレス カーボン コピーを電子メールのセミコロン区切りのリストです。 コピーの受信者リストのデータ型**varchar (max)** します。 このパラメーターは省略可能な少なくとも 1 つの **@recipients** 、 **@copy_recipients** 、または **@blind_copy_recipients** 指定する必要がありますまたは**sp _send_dbmail**はエラーを返します。  
  
`[ @blind_copy_recipients = ] 'blind_copy_recipients'` メッセージをアドレス ブラインド カーボン コピーを電子メールのセミコロン区切りのリストです。 ブラインド コピーの受信者リストのデータ型**varchar (max)** します。 このパラメーターは省略可能な少なくとも 1 つの **@recipients** 、 **@copy_recipients** 、または **@blind_copy_recipients** 指定する必要がありますまたは**sp _send_dbmail**はエラーを返します。  
  
`[ @from_address = ] 'from_address'` 値は、電子メール メッセージのアドレス' から'。 これは、メール プロファイルの設定をオーバーライドするために使用する省略可能なパラメーターです。 このパラメーターは型**varchar (max)** します。 オーバーライドが許可されるかどうかは、SMTP のセキュリティ設定によって決まります。 パラメーターが指定されていない場合、既定値は NULL です。  
  
`[ @reply_to = ] 'reply_to'` 返信先アドレス' 電子メール メッセージの値です。 有効な値として 1 つだけの電子メール アドレスを受け入れます。 これは、メール プロファイルの設定をオーバーライドするために使用する省略可能なパラメーターです。 このパラメーターは型**varchar (max)** します。 オーバーライドが許可されるかどうかは、SMTP のセキュリティ設定によって決まります。 パラメーターが指定されていない場合、既定値は NULL です。  
  
`[ @subject = ] 'subject'` 電子メール メッセージの件名です。 件名は、型の**nvarchar (255)** します。 サブジェクトが指定されていない場合は、既定では 'SQL Server メッセージ' です。  
  
`[ @body = ] 'body'` 電子メール メッセージの本文に示します。 型のメッセージの本文は、 **nvarchar (max)** 、既定値は NULL です。  
  
`[ @body_format = ] 'body_format'` メッセージ本文の形式です。 型のパラメーターが**varchar (20)** 、既定値は NULL です。 指定した場合、送信メッセージのヘッダーには、メッセージの本文が指定の形式であることを示す文字列が設定されます。 パラメーターには、次の値のいずれかを含めることができます。  
  
-   [TEXT]  
  
-   HTML (HTML)  
  
 既定値はテキストです。  
  
`[ @importance = ] 'importance'` メッセージの重要度です。 型のパラメーターが**varchar (6)** します。 パラメーターには、次の値のいずれかを含めることができます。  
  
-   Low  
  
-   標準  
  
-   高  
  
 既定値は Normal です。  
  
`[ @sensitivity = ] 'sensitivity'` メッセージの機密性です。 型のパラメーターが**varchar (12)** します。 パラメーターには、次の値のいずれかを含めることができます。  
  
-   標準  
  
-   個人用  
  
-   プライベート  
  
-   社外秘  
  
 既定値は Normal です。  
  
`[ @file_attachments = ] 'file_attachments'` 電子メール メッセージに添付するファイル名のセミコロン区切りの一覧を示します。 リスト内のファイルは、絶対パスとして指定する必要があります。 添付ファイル リストのデータ型**nvarchar (max)** します。 既定では、データベース メールの添付ファイルは 1 ファイルにつき 1 MB に制限されます。  
  
`[ @query = ] 'query'` クエリの実行です。 クエリの結果をファイルとして添付または電子メール メッセージの本文に含めることがことができます。 クエリの種類のデータ**nvarchar (max)** 、任意の有効なを含めることができる[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント。 別のセッション スクリプトの呼び出しのためのローカル変数で、クエリが実行されることに注意してください。 **sp_send_dbmail**は、クエリを使用できません。  
  
`[ @execute_query_database = ] 'execute_query_database'` ストアド プロシージャがクエリを実行するデータベースのコンテキストです。 型のパラメーターが**sysname**、現在のデータベースの既定値。 このパラメーターはのみに適用される場合 **@query** を指定します。  
  
`[ @attach_query_result_as_file = ] attach_query_result_as_file` 添付ファイルとして、クエリの結果セットを返すかどうかを指定します。 *attach_query_result_as_file*の種類は**ビット**、既定値は 0。  
  
 内容の後、クエリの結果が、電子メール メッセージの本文に含まれる値が 0 の場合、 **@body** パラメーター。 値が 1 の場合は、添付ファイルとして結果が返されます。 このパラメーターはのみに適用される場合 **@query** を指定します。  
  
`[ @query_attachment_filename = ] query_attachment_filename` クエリの添付ファイルの結果セットを使用するファイル名を指定します。 *query_attachment_filename*の種類は**nvarchar (255)** 、既定値は NULL です。 このパラメーターは無視されますと*attach_query_result*は 0 です。 ときに*attach_query_result* 1 で、このパラメーターが null の場合、データベース メールは、任意のファイル名を作成します。  
  
`[ @query_result_header = ] query_result_header` クエリの結果が列のヘッダーを含めるかどうかを指定します。 Query_result_header 値の型は**ビット**します。 値が 1 の場合は、クエリの結果に列ヘッダーが含まれます。 値が 0 の場合、クエリの結果には列のヘッダーは含まれません。 このパラメーターの既定値**1**します。 このパラメーターはのみに適用される場合 **@query** を指定します。  
 
   >[!NOTE]
   > 設定するときに、次のエラーが発生する@query_result_header0 と設定に@query_no_truncate1。
   > <br> Msg 22050、レベル 16、状態 1、12 行目。エラー番号-2147024809 使用して sqlcmd ライブラリを初期化できませんでした。
  
`[ @query_result_width = ] query_result_width` クエリの結果を書式設定するために使用する、文字で、線の幅です。 *Query_result_width*の種類は**int**、既定値は 256 です。 指定された値は 10 ~ 32767 の間にある必要があります。 このパラメーターはのみに適用される場合 **@query** を指定します。  
  
`[ @query_result_separator = ] 'query_result_separator'` クエリ出力に列を区切るために使用する文字。 型の区切り記号は**char (1)** します。 既定値は '' (スペース)。  
  
`[ @exclude_query_output = ] exclude_query_output` 電子メール メッセージで、クエリの実行の出力を返すかどうかを指定します。 **exclude_query_output**ビットは、既定値は 0。 このパラメーターが 0 の場合の実行の場合、 **sp_send_dbmail**ストアド プロシージャは、コンソールで、クエリの実行の結果として返されるメッセージを出力します。 このパラメーターが 1 での実行の場合、 **sp_send_dbmail**ストアド プロシージャが印刷されないクエリの実行のメッセージのいずれかのコンソールにします。  
  
`[ @append_query_error = ] append_query_error` 指定されたクエリからエラーが返されるときに電子メールを送信するかどうかを指定します、 **@query** 引数。 **append_query_error**は**ビット**、既定値は 0。 このパラメーターが 1 の場合、データベース メールは電子メール メッセージを送信し、電子メール メッセージの本文にクエリのエラー メッセージが含まれています。 データベース メールで電子メール メッセージを送信しませんこのパラメーターが 0 の場合と**sp_send_dbmail**失敗を示すリターン コード 1 で終了します。  
  
`[ @query_no_truncate = ] query_no_truncate` 長い可変長データ型の切り捨てを回避するオプションを使用してクエリを実行するかどうかを指定します (**varchar (max)** 、 **nvarchar (max)** 、 **varbinary (max)** 、 **xml**、**テキスト**、 **ntext**、**イメージ**、およびユーザー定義データ型)。 設定すると、クエリの結果では列のヘッダーを含めることはできません。 *Query_no_truncate*値の型は**ビット**します。 値が 0 の場合や指定されていない場合、クエリ内の列は 256 文字に切り捨てられます。 値が 1 の場合は、クエリ内の列は切り捨てられません。 このパラメーターの既定値は 0。  
  
> [!NOTE]  
>  大量のデータを使用すると、@**query_no_truncate**オプションは、追加のリソースを消費し、サーバーのパフォーマンスが低下することができます。  
  
`[ @query_result_no_padding ] @query_result_no_padding` 型は bit です。 既定値は 0 です。 1 に設定すると、クエリ結果埋め込みは行われません、ファイルのサイズを減らす可能性があります。設定した場合@query_result_no_paddingを 1 に設定、@query_result_widthパラメーター、@query_result_no_paddingパラメーターの上書き、@query_result_widthパラメーター。  
  
 ここではエラーは発生しません。  
 
  >[!NOTE]
  > 設定するときに、次のエラーが発生する@query_result_no_padding1 からのパラメーターを指定するには @query_no_truncate:
  > <br> メッセージ 22050、レベル 16、状態 1、0 行目。クエリを実行できませんでした、@query_result_no_appendと@query_no_truncateオプションは相互に排他的です。 
  
 設定した場合、@query_result_no_paddingを 1 に設定、@query_no_truncateパラメーター、エラーが発生します。  
  
`[ @mailitem_id = ] mailitem_id [ OUTPUT ]` 省略可能な出力パラメーターを返します、 *mailitem_id*メッセージ。 *Mailitem_id*の種類は**int**します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 リターン コードが 0 の場合は成功を示します。 その他の値は、障害を意味します。 失敗したステートメントのエラー コードは、@@ERROR変数。  
  
## <a name="result-sets"></a>結果セット  
 成功すると、"メールがキューに登録されました。" というメッセージが返されます。  
  
## <a name="remarks"></a>コメント  
 を使用する前にデータベース メールを有効に、データベース メール構成ウィザードを使用してまたは**sp_configure**します。  
  
 **sysmail_stop_sp**データベース メール外部プログラムが使用する Service Broker オブジェクトの停止を停止します。 **sp_send_dbmail**を使用してデータベース メールが停止したときにメールを受け付ける**sysmail_stop_sp**します。 データベース メールを開始するには使用**sysmail_start_sp**します。  
  
 ときに **@profile** が指定されていない**sp_send_dbmail**既定プロファイルが使用されます。 電子メール メッセージを送信するユーザーに既定のプライベート プロファイルがある場合、データベース メールではそのプロファイルが使用されます。 ユーザーが既定のプライベート プロファイルを持たない場合**sp_send_dbmail**既定パブリック プロファイルを使用します。 ユーザーの既定のプライベート プロファイルと、既定のパブリック プロファイルが存在しない場合**sp_send_dbmail**はエラーを返します。  
  
 **sp_send_dbmail**内容のない電子メール メッセージをサポートしていません。 電子メール メッセージを送信するの少なくとも 1 つを指定する必要があります **@body** 、 **@query** 、 **@file_attachments** 、または **@subject** . それ以外の場合、 **sp_send_dbmail**はエラーを返します。  
  
 データベース メールでは、ファイルへのアクセス制御に現在のユーザーの [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows セキュリティ コンテキストが使用されます。 そのため、認証されたユーザーがで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証を使用してファイルをアタッチできません **@file_attachments** します。 Windows では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用してリモート コンピューター間で資格情報を交換することは許可されません。 そのため、データベース メールできない場合は、コマンドを実行して、コンピューター以外のコンピューターからネットワーク共有からファイルを添付する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上で実行します。  
  
 両方 **@query** と **@file_attachments** は指定されたファイルが見つからないと、クエリは実行されますが、電子メールは送信されません。  
  
 クエリを指定すると、結果セットはインライン テキストとして書式設定します。 結果セットにあるバイナリ データは 16 進数形式で送信されます。  
  
 パラメーター **@recipients** 、 **@copy_recipients** 、および **@blind_copy_recipients** は電子メール アドレスのセミコロン区切りのリスト。 これらのパラメーターの少なくとも 1 つを指定する必要があります、または**sp_send_dbmail**はエラーを返します。  
  
 実行時に**sp_send_dbmail**トランザクションのコンテキストなしデータベース メールが開始され、暗黙のトランザクションをコミットします。 実行時に**sp_send_dbmail**から既存のトランザクション内でデータベース メールはユーザーのコミットまたは変更をロールバックします。 内側のトランザクションは開始されません。  
  
## <a name="permissions"></a>アクセス許可  
 実行権限**sp_send_dbmail**の既定値のすべてのメンバーは、 **DatabaseMailUser**データベース ロール、 **msdb**データベース。 ただし、ときに、メッセージを送信するユーザーは権限がありません、要求のプロファイルを使用する**sp_send_dbmail**エラーが返され、メッセージを送信しません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-sending-an-e-mail-message"></a>A. 電子メール メッセージを送信します。  
 この例では、電子メール メッセージを送信する電子メール アドレスを使用して、友人`myfriend@Adventure-Works.com`します。 メッセージの件名`Automated Success Message`します。 メッセージの本文には、文が含まれています。`'The stored procedure finished successfully'`します。  
  
```  
EXEC msdb.dbo.sp_send_dbmail  
    @profile_name = 'Adventure Works Administrator',  
    @recipients = 'yourfriend@Adventure-Works.com',  
    @body = 'The stored procedure finished successfully.',  
    @subject = 'Automated Success Message' ;  
```  
  
### <a name="b-sending-an-e-mail-message-with-the-results-of-a-query"></a>B. 電子メール メッセージをクエリの結果と共に送信する  
 この例では、電子メール メッセージを送信する電子メール アドレスを使用して、友人`yourfriend@Adventure-Works.com`します。 メッセージの件名は `Work Order Count` で、このメッセージでは `DueDate` が 2004 年 4 月 30 日から 2 日以内となっている作業指示の番号を表示するクエリが実行されます。 データベース メールでは、テキスト ファイルとして結果をアタッチします。  
  
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
  
### <a name="c-sending-an-html-e-mail-message"></a>C. HTML 電子メール メッセージを送信します。  
 この例では、電子メール メッセージを送信する電子メール アドレスを使用して、友人`yourfriend@Adventure-Works.com`します。 メッセージの件名`Work Order List`、作業注文を表示する HTML ドキュメントが含まれています、 `DueDate` 2 日以内、2004 年 4 月 30 日後。 データベース メールでは、このメッセージが HTML 形式で送信されます。  
  
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
  
## <a name="see-also"></a>関連項目  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール構成オブジェクト](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [データベース メール ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)  
  
  
