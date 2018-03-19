---
title: RESTORE REWINDONLY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/10/2017
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
- RESTORE_REWINDONLY_TSQL
- RESTORE REWINDONLY
dev_langs:
- TSQL
helpviewer_keywords:
- closing backup devices
- backup devices [SQL Server], rewinding
- media [SQL Server]
- open back devices
- rewinding backup devices
- RESTORE REWINDONLY statement
ms.assetid: 7f825b40-2264-4608-9809-590d0f09d882
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bf67d54e58f08296878c0781158e7b878b0b2a49
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="restore-statements---rewindonly-transact-sql"></a>RESTORE ステートメント - REWINDONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  NOREWIND オプションで実行された BACKUP または RESTORE ステートメントにより、開かれたままとなっていた特定のテープ デバイスを巻き戻して閉じます。 このコマンドはテープ デバイスに対してのみサポートされています。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
RESTORE REWINDONLY   
FROM <backup_device> [ ,...n ]  
[ WITH {UNLOAD | NOUNLOAD}]  
}   
[;]  
  
<backup_device> ::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
   | TAPE = { 'physical_backup_device_name' |  
       @physical_backup_device_name_var }   
}   
```  
  
## <a name="arguments"></a>引数  
 **\<backup_device> ::=** 
  
 復元操作に使用する、論理バックアップ デバイスまたは物理バックアップ デバイスを指定します。  
  
 { *logical_backup_device_name* | **@***logical_backup_device_name_var* } Is the logical name, which must follow the rules for identifiers, of the backup devices created by **sp_addumpdevice** from which the database is restored.変数 (**@***logical_backup_device_name_var*) として指定する場合、バックアップ デバイス名は、文字列定数 (**@***logical_backup_device_name_var* = *logical_backup_device_name*) として、または **ntext** や **text** データ型を除く、文字の文字列データ型の変数として指定できます。  
  
 {DISK | TAPE } **=** { **'***physical_backup_device_name***'** | **@***physical_backup_device_name_var* } 名前付きのディスクまたはテープ デバイスからバックアップを復元することを許可します。ディスクまたはテープを表すデバイスの種類を、完全なパスとファイル名を含む実際のデバイス名と共に指定してください。たとえば、DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL\BACKUP\Mybackup.bak' or TAPE = '\\\\.\TAPE0' のように指定します。変数 (**@***physical_backup_device_name_var*) として指定する場合、デバイス名は、文字列定数 (**@***physical_backup_device_name_var* = '*physcial_backup_device_name*') として、または **ntext** や **text** データ型を除く、文字の文字列データ型の変数として指定できます。  
  
 ネットワーク サーバーを UNC 名で指定する場合は、デバイスの種類に DISK を指定してください (UNC 名にはマシン名を含める必要があります)。 UNC 名の使用の詳細については、「[バックアップ デバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)」を参照してください。  
  
 RESTORE 操作を実行するには、Microsoft SQL&amp;#xA0;Server を実行するアカウントに、リモート コンピューターまたはネットワーク サーバーへの読み取りアクセス権が与えられている必要があります。  
  
 *n*  
 複数のバックアップ デバイスと論理バックアップ デバイスを指定できることを示すプレースホルダーです。 **64** 個までのバックアップ デバイスまたは論理バックアップ デバイスを指定できます。  
  
 復元シーケンスで必要になるバックアップ デバイスの数が、バックアップが含まれるメディア セットの作成で使用したデバイスの数と同じになるかどうかは、復元をオフラインとオンラインのどちらで行うかによって決まります。 オフライン復元の場合は、バックアップの作成時よりも少ない数のデバイスでバックアップを復元できます。 オンライン復元の場合は、バックアップの作成時に使用されたすべてのバックアップ デバイスが必要です。 それより少ない数のデバイスで復元しようとしても失敗します。  
  
 詳細については、「 [バックアップ デバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)の別のインスタンスで作成された場合、これは必須です。  
  
> [!NOTE]  
>  ミラー化されたメディア セットからバックアップを復元する場合は、各メディア ファミリに対して 1 つのミラーだけを指定できますが、 エラーが発生したとき、他に複数のミラーを用意しておくと復元に関する問題をすばやく解決できる場合があります。 損傷したメディア ボリュームは、別のミラーの対応するボリュームで代替できます。 オフライン復元の場合は、メディア ファミリの数よりも少ない数のデバイスから復元できますが、各ファミリは一度しか処理されないことに注意してください。  
  
 **WITH オプション**  
  
 UNLOAD  
 RESTORE 完了後に、テープの巻き戻しとアンロードを自動的に行うことを指定します。 既定では、新しいユーザー セッションを開始すると UNLOAD が設定されます。 UNLOAD の設定は、NOUNLOAD が指定されるまで有効です。 このオプションはテープ デバイスに対してのみ使用できます。 RESTORE にテープ以外のデバイスが指定されている場合、このオプションは無視されます。  
  
 NOUNLOAD  
 RESTORE 完了後に、テープをテープ デバイスから自動的にアンロードしないことを指定します。 NOUNLOAD の設定は、UNLOAD が指定されるまで有効です。  
  
 RESTORE 完了後に、テープをテープ デバイスから自動的にアンロードしないことを指定します。 NOUNLOAD の設定は、UNLOAD が指定されるまで有効です。  
  
## <a name="general-remarks"></a>全般的な解説  
 RESTORE REWINDONLY は、RESTORE LABELONLY FROM TAPE = \<name> WITH REWIND の代わりに使用できます。 [sys.dm_io_backup_tapes](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md) 動的管理ビューを使用すると、開いているテープ ドライブの一覧を確認できます。  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 すべてのユーザーが RESTORE REWINDONLY を使用できます。  
  
## <a name="see-also"></a>参照  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [バックアップの履歴とヘッダーの情報 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  

