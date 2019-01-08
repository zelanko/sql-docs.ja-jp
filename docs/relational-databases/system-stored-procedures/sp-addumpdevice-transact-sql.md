---
title: sp_addumpdevice (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addumpdevice_TSQL
- sp_addumpdevice
dev_langs:
- TSQL
helpviewer_keywords:
- backup devices [SQL Server], defining
- sp_addumpdevice
ms.assetid: c2d2ae49-0808-46d8-8444-db69a69d0ec3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d43074e9cdffa27e971d32278259001ae86c005f
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53209451"
---
# <a name="spaddumpdevice-transact-sql"></a>sp_addumpdevice (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[現在のバージョン](https://go.microsoft.com/fwlink/p/?LinkId=299658))。  

バックアップ デバイスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに追加します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addumpdevice [ @devtype = ] 'device_type'   
    , [ @logicalname = ] 'logical_name'   
    , [ @physicalname = ] 'physical_name'  
      [ , { [ @cntrltype = ] controller_type |  
          [ @devstatus = ] 'device_status' }  
      ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@devtype=** ] **'***device_type***'**  
 バックアップ デバイスの種類を指定します。 *device_type*は**varchar (20)**, で、既定値はありませんは、次の値のいずれかを指定します。  
  
|値|説明|  
|-----------|-----------------|  
|**disk**|バックアップ デバイスとしてのハード ディスク ファイル。|  
|**tape**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows でサポートされるテープ デバイス。<br /><br /> 注:テープ バックアップ デバイスは、将来のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でサポートされなくなる予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。|  
  
 [ **@logicalname =** ] **'***logical_name***'**  
 BACKUP ステートメントおよび RESTORE ステートメントで使用するバックアップ デバイスの論理名を指定します。 *logical_name*は**sysname**、既定値はありません、NULL にすることはできません。  
  
 [ **@physicalname =** ] **'***physical_name***'**  
 バックアップ デバイスの物理名を指定します。 物理名にはオペレーティング システムのファイル名の規則またはネットワーク デバイスの UNC (汎用名前付け規則) が適用されます。物理名には完全パスを指定する必要があります。 *physical_name*は**nvarchar (260)**、既定値はありません値に設定して、NULL にすることはできません。  
  
 リモート ネットワーク上にバックアップ デバイスを作成する場合は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]を起動した名前でそのリモート コンピューター上に書き込むことができるか確認してください。  
  
 テープ デバイスを追加する場合は、このパラメーターが Windows; でローカル テープ デバイスに割り当てられている物理名を指定する必要があります。たとえば、  **\\ \\. \TAPE0**のコンピューター上の最初のテープ デバイス。 テープ デバイスは、必ずサーバー コンピューターに接続してください。リモートからは使用できません。 英数字以外の文字を含む名前は、引用符で囲みます。  
  
> [!NOTE]  
>  このプロシージャでは、指定された物理名がカタログに入力されます。 プロシージャがデバイスへのアクセスや作成を試みることはありません。  
  
 [  **@cntrltype =** ] **'***controller_type***'**  
 互換性のために残されています。 このパラメーターを指定しても無視されます。 旧バージョンとの互換性のためだけに用意されています。 初めて使用**sp_addumpdevice**このパラメーターを省略する必要があります。  
  
 [  **@devstatus =** ] **'***device_status***'**  
 互換性のために残されています。 このパラメーターを指定しても無視されます。 旧バージョンとの互換性のためだけに用意されています。 初めて使用**sp_addumpdevice**このパラメーターを省略する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 **sp_addumpdevice**にバックアップ デバイスの追加、 **sys.backup_devices**カタログ ビューです。 その後、そのデバイスを BACKUP ステートメントや RESTORE ステートメントで論理的に参照できるようになります。 **sp_addumpdevice**物理デバイスへのアクセスは行われません。 BACKUP ステートメントや RESTORE ステートメントが実行されるときにだけ、指定されたデバイスにアクセスされます。 論理バックアップ デバイスを作成すると、デバイス パスの指定時にデバイス名を指定する代わりに "TAPE =" 句や "DISK =" 句を指定できるので、BACKUP ステートメントや RESTORE ステートメントを簡素化できます。  
  
 ディスクまたはファイルのバックアップ デバイスを使用する場合は、所有権や権限が問題になることがあります。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]を起動する Windows アカウントに適切なファイル権限が付与されているかどうかを確認してください。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]では、Windows でサポートされているテープ デバイスへのバックアップがサポートされます。 Windows でサポートされるテープ デバイスの詳細については、Windows のハードウェア互換性リストを参照してください。 コンピューターで使用できるテープ デバイスを表示するには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用します。  
  
 各テープ ドライブのメーカーが推奨するテープ以外は使用しないでください。 DAT (digital audio tape) ドライブを使用している場合は、コンピューター用の DAT テープ (Digital Data Storage-DDS) を使用してください。  
  
 **sp_addumpdevice**トランザクション内で実行することはできません。  
  
 デバイスを削除するには使用[sp_dropdevice](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)または[SQL Server Management Studio](../../relational-databases/backup-restore/delete-a-backup-device-sql-server.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 **diskadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
 ディスクに対する書き込み権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-adding-a-disk-dump-device"></a>A. ディスク ダンプ デバイスを追加する  
 次の例では、`mydiskdump` というディスク バックアップ デバイスを物理名 `c:\dump\dump1.bak` で追加します。  
  
```  
USE master;  
GO  
EXEC sp_addumpdevice 'disk', 'mydiskdump', 'c:\dump\dump1.bak';  
```  
  
### <a name="b-adding-a-network-disk-backup-device"></a>B. ネットワーク ディスク バックアップ デバイスを追加する  
 次の例では、`networkdevice` というリモートのディスク バックアップ デバイスを追加します。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]を起動する名前には、そのリモート ファイル (`\\<servername>\<sharename>\<path>\<filename>.bak`) を扱う権限が必要です。  
  
```  
USE master;  
GO  
EXEC sp_addumpdevice 'disk', 'networkdevice',  
    '\\<servername>\<sharename>\<path>\<filename>.bak';  
```  
  
### <a name="c-adding-a-tape-backup-device"></a>C. テープ バックアップ デバイスを追加する  
 次の例では、`tapedump1` デバイスを物理名 `\\.\tape0` で追加します。  
  
```  
USE master;  
GO  
EXEC sp_addumpdevice 'tape', 'tapedump1', '\\.\tape0';  
```  
  
### <a name="d-backing-up-to-a-logical-backup-device"></a>D. 論理バックアップ デバイスにバックアップする  
 次の例では、バックアップ ディスク ファイル用の論理バックアップ デバイス `AdvWorksData` を作成した後、 作成した論理バックアップ デバイスに [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースをバックアップします。  
  
```  
USE master;  
GO  
EXEC sp_addumpdevice 'disk', 'AdvWorksData',   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\BACKUP\AdvWorksData.bak';  
GO  
BACKUP DATABASE AdventureWorks2012   
 TO AdvWorksData  
   WITH FORMAT;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [バックアップ デバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [ディスク ファイルの論理バックアップ デバイスの定義 &#40;SQL Server&#41;](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-disk-file-sql-server.md)   
 [テープ ドライブの論理バックアップ デバイスの定義 &#40;SQL Server&#41;](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-tape-drive-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [sp_dropdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [sys.backup_devices &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
