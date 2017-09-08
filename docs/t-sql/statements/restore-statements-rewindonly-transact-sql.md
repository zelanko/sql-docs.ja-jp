---
title: "RESTORE REWINDONLY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 50
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 731cb91434fcf193d7a3391151400942061dfd21
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="restore-statements---rewindonly-transact-sql"></a>RESTORE ステートメントで REWINDONLY (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 **\<backup_device >:: =** 
  
 復元操作に使用する、論理バックアップ デバイスまたは物理バックアップ デバイスを指定します。  
  
 { *logical_backup_device_name* | **@***logical_backup_device_name_var* }  
 によって作成されたバックアップ デバイスの識別子の規則に従う必要があります、論理名は、 **sp_addumpdevice**からデータベースを復元します。 変数として指定する場合 (**@***logical_backup_device_name_var*)、バックアップ デバイス名を指定できます文字列定数として指定 ( **@** *logical_backup_device_name_var* = *logical_backup_device_name*) または文字の文字列データ型の変数として以外の**ntext**または**テキスト**データ型。  
  
 {ディスク |テープ}  **=**  { **'***physical_backup_device_name***'**  |   **@** *physical_backup_device_name_var* }  
 指定したディスク デバイスまたはテープ デバイスから、バックアップを復元することを許可します。 デバイスの実際の名前 (たとえば、完全なパスとファイル名) でディスクとテープのデバイスの種類を指定する必要があります。 ディスク = 'C:\Program files \microsoft SQL Server\MSSQL\BACKUP\Mybackup.bak' や TAPE ='\\\\。 \TAPE0' です。 変数として指定されている場合 (**@***physical_backup_device_name_var*)、デバイス名を指定できます文字列定数として指定 ( **@**  *physical_backup_device_name_var* = '*physcial_backup_device_name*') または文字の文字列データ型の変数として以外の**ntext**または**テキスト**データ型。  
  
 ネットワーク サーバーを UNC 名で指定する場合は、デバイスの種類に DISK を指定してください (UNC 名にはマシン名を含める必要があります)。 UNC 名の使用の詳細については、次を参照してください。[バックアップ デバイス & #40 です。SQL Server &#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
 Microsoft SQL Server を実行しているアカウントによっては、復元操作を実行するために、リモート コンピューターまたはネットワーク サーバーへの読み取りアクセスが必要です。  
  
 *n*  
 複数のバックアップ デバイスと論理バックアップ デバイスを指定できることを示すプレースホルダーです。 バックアップ デバイスまたは論理バックアップ デバイスの最大数は**64**です。  
  
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
 RESTORE REWINDONLY は、代わりに RESTORE LABELONLY FROM TAPE = \<name > WITH REWIND です。 開いているテープ ドライブの一覧を取得できる、 [sys.dm_io_backup_tapes](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md)動的管理ビュー。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 すべてのユーザーが RESTORE REWINDONLY を使用できます。  
  
## <a name="see-also"></a>参照  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [バックアップの履歴とヘッダーの情報 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  


