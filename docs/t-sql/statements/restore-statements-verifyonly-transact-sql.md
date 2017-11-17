---
title: "RESTORE VERIFYONLY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VERIFYONLY
- RESTORE VERIFYONLY
- VERIFYONLY_TSQL
- RESTORE_VERIFYONLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RESTORE VERIFYONLY statement
- backups [SQL Server], verifying
- verifying backups
- checking backups
ms.assetid: cba3b6a0-b48e-4c94-812b-5b3cbb408bd6
caps.latest.revision: 64
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6996997ff66c291285fef4081dc7c21477ea8584
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="restore-statements---verifyonly-transact-sql"></a>RESTORE ステートメントで VERIFYONLY (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  復元せずにバックアップを確認して、バックアップ セットが完全なものであること、およびバックアップのすべてが読み取り可能であることを確認します。 ただし、RESTORE VERIFYONLY ステートメントが、バックアップ ボリュームに含まれているデータの構造を確認することはありません。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラーの検出率を向上させるデータに対して追加のチェックを行う RESTORE VERIFYONLY が強化されました。 この機能の目的は、実際の復元操作にできるだけ近い状況を実現することです。 詳細については、「解説」を参照してください。  
  
 バックアップが、有効な場合は、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]成功メッセージが返されます。  
  
> [!NOTE]  
>  引数の説明については、次を参照してください。 [RESTORE の引数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
RESTORE VERIFYONLY  
FROM <backup_device> [ ,...n ]  
[ WITH    
 {  
   LOADHISTORY   
  
--Restore Operation Option  
 | MOVE 'logical_file_name_in_backup' TO 'operating_system_file_name'   
          [ ,...n ]   
  
--Backup Set Options  
 | FILE = { backup_set_file_number | @backup_set_file_number }   
 | PASSWORD = { password | @password_variable }   
  
--Media Set Options  
 | MEDIANAME = { media_name | @media_name_variable }   
 | MEDIAPASSWORD = { mediapassword | @mediapassword_variable }  
  
--Error Management Options  
 | { CHECKSUM | NO_CHECKSUM }   
 | { STOP_ON_ERROR | CONTINUE_AFTER_ERROR }  
  
--Monitoring Options  
 | STATS [ = percentage ]   
  
--Tape Options  
 | { REWIND | NOREWIND }   
 | { UNLOAD | NOUNLOAD }    
 } [ ,...n ]  
]  
[;]  
  
<backup_device> ::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
   | { DISK | TAPE } = { 'physical_backup_device_name' |  
       @physical_backup_device_name_var }   
}  
  
```  
  
## <a name="arguments"></a>引数  
 RESTORE VERIFYONLY の引数の説明については、次を参照してください。 [RESTORE の引数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="general-remarks"></a>全般的な解説  
 メディア セットまたはバックアップ セットには、Microsoft Tape Format として解釈できるように最小限の正しい情報が含まれている必要があります。 含まれていない場合は、RESTORE VERIFYONLY が停止し、バックアップの形式が無効であることが示されます。  
  
 RESTORE VERIFYONLY で実行される確認項目には、次のようなものがあります。  
  
-   バックアップ セットが完全で、すべてのボリュームが読み取り可能であること。  
  
-   ページ ID など、データベース ページのヘッダー フィールドの情報 (データ書き込みを想定した確認)。  
  
-   チェックサム (メディアに存在する場合)。  
  
-   バックアップ先デバイスに十分な容量があるかどうか。  
  
> [!NOTE]  
>  RESTORE VERIFYONLY は、データベース スナップショットでは動作しません。 元に戻す操作を行う前にデータベース スナップショットを確認するには、DBCC CHECKDB を実行してください。  
  
> [!NOTE]  
>  スナップショットのバックアップでは、RESTORE VERIFYONLY は、バックアップ ファイルで指定された場所にスナップショットの存在を確認します。 スナップショット バックアップは新しい機能で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]です。 スナップショット バックアップの詳細については、次を参照してください。 [Azure でのデータベース ファイルのファイル スナップショット バックアップ](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)です。  
  
## <a name="security"></a>セキュリティ  
 バックアップ操作では、オプションで、メディア セットとバックアップ セットにそれぞれパスワードを設定できます。 メディア セットまたはバックアップ セットにパスワードが設定されている場合は、RESTORE ステートメントで正しいパスワードを指定する必要があります。 これらのパスワードが不正に復元操作を防ぐため、不正なメディアを使用するバックアップ セットの追加[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ツールです。 ただし、BACKUP ステートメントで FORMAT オプションが使用された場合、メディアの上書きを防ぐことはできません。  
  
> [!IMPORTANT]  
>  パスワードによる保護は強力なものではありません。 使用して、正しくない復元を防止するものでは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ツールを承認またはユーザーです。 その他の手段によるバックアップ データの読み取りやパスワードの置き換えを防ぐわけではありません。 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]バックアップを保護するためのベスト プラクティスでは、安全な場所に、または十分なアクセス制御リスト (Acl) によって保護されているディスク ファイルへのバックアップ、バックアップ テープを保存します。 ACL は、バックアップを作成するディレクトリのルートに設定する必要があります。  
  
### <a name="permissions"></a>Permissions  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは、バックアップ セットやバックアップ デバイスに関する情報の取得には CREATE DATABASE 権限が必要になります。 詳細については、「[GRANT (データベースの権限の許可) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE REWINDONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [バックアップの履歴とヘッダーの情報 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  

