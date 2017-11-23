---
title: "backupmediaset (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- backupmediaset
- backupmediaset_TSQL
dev_langs: TSQL
helpviewer_keywords:
- backup media [SQL Server], backupmediaset system table
- backupmediaset system table
ms.assetid: d9c18a93-cab9-4db8-ae09-c6bd8145ab8f
caps.latest.revision: "39"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4e86380a170009fbfd8ee7fd2f891dc210cab856
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="backupmediaset-transact-sql"></a>backupmediaset (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  バックアップ メディア セットごとに 1 行のデータを格納します。 次の表は、 **msdb**データベース。  
 
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**media_set_id**|**int**|一意なメディア セット識別番号。 ID、主キー。|  
|**media_uuid**|**uniqueidentifier**|メディア セットの UUID。 すべて[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UUID をあるメディア セット。<br /><br /> 以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ただし、メディア セットには、1 つのメディア ファミリが含まれている場合、 **media_uuid**列は NULL になります (**media_family_count**は 1)。|  
|**media_family_count**|**tinyint**|メディア セット内のメディア ファミリの数。 NULL にすることができます。|  
|**name**|**nvarchar (128)**|メディア セットの名前。 NULL にすることができます。<br /><br /> 詳細についてを参照してください MEDIANAME と MEDIADESCRIPTION[バックアップ &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/backup-transact-sql.md).|  
|**説明**|**nvarchar (255)**|メディア セットの説明。 NULL にすることができます。<br /><br /> 詳細についてを参照してください MEDIANAME と MEDIADESCRIPTION[バックアップ &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/backup-transact-sql.md).|  
|**software_name**|**nvarchar (128)**|メディア ラベルを記述したバックアップ ソフトウェアの名前。 NULL にすることができます。|  
|**software_vendor_id**|**int**|バックアップ メディア ラベルを記述したソフトウェア ベンダーの識別番号。 NULL にすることができます。<br /><br /> 値は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は 16 進数の 0x1200 です。|  
|**MTF_major_version**|**tinyint**|メジャー バージョン番号の[!INCLUDE[msCoName](../../includes/msconame-md.md)]Tape Format は、このメディア セットの生成に使用します。 NULL にすることができます。|  
|**mirror_count**|**tinyint**|メディア セットのミラー数。|  
|**is_password_protected**|**bit**|メディア セットのパスワードが保護されているかどうか。<br /><br /> 0 = 保護されていない<br /><br /> 1 = 保護されている|  
|**is_compressed**|**bit**|バックアップが圧縮されているかどうか。<br /><br /> 0 = 非圧縮<br /><br /> 1 = 圧縮<br /><br /> 中に、 **msdb**アップグレードすると、この値は NULL に設定します。 これは圧縮されていないバックアップを示します。|  
|**is_encrypted**|**ビット**|バックアップが暗号化されているかどうか。<br /><br /> 0 = 暗号化されていません。<br /><br /> 1 = 暗号化|  
  
## <a name="remarks"></a>解説  
 RESTORE VERIFYONLY FROM *backup_device* WITH LOADHISTORY の列に設定、 **backupmediaset**メディア セット ヘッダーから適切な値を持つテーブルです。  
  
 次の表では他のバックアップと履歴テーブルの行の数を減らすためには、実行、 [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)ストアド プロシージャです。  
  
## <a name="see-also"></a>参照  
 [バックアップと復元のテーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [システム テーブルと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
