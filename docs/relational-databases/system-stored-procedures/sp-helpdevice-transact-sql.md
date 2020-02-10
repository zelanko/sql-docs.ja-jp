---
title: sp_helpdevice (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpdevice
- sp_helpdevice_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdevice
ms.assetid: 1a5eafa7-384e-4691-ba05-978eb73bbefb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0db0242e5bdd9e04d3d7c424382933121c2e0ac2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67902989"
---
# <a name="sp_helpdevice-transact-sql"></a>sp_helpdevice (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Microsoft&#xAE; SQL Server&#x2122; のバックアップ デバイスに関する情報をレポートします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに、backup_devices カタログビューを使用することをお勧めし[ます。](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md)  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpdevice [ [ @devname = ] 'name' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @devname = ] 'name'`情報を報告するバックアップデバイスの名前を指定します。 *Name*の値は常に**sysname**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**device_name**|**sysname**|論理デバイス名。|  
|**physical_name**|**nvarchar (260)**|物理ファイル名。|  
|**記述**|**nvarchar(255)**|デバイスの説明|  
|**オンライン**|**int**|[**説明**列の状態の説明に対応する数値。|  
|**cntrltype**|**smallint**|デバイスのコントローラーの種類<br /><br /> 2 = ディスク デバイス<br /><br /> 5 = テープデバイス|  
|**幅**|**int**|デバイスサイズ (2 KB ページ単位)。|  
  
## <a name="remarks"></a>解説  
 *名前*を指定した場合、 **sp_helpdevice**指定したダンプデバイスに関する情報が表示されます。 場合*名前*が指定されていない、 **sp_helpdevice** 、すべてのダンプデバイスに関する情報を表示、 **backup_devices**カタログビューです。  
  
 ダンプデバイスは**sp_addumpdevice**を使用してシステムに追加されます。  
  
## <a name="permissions"></a>アクセス許可  
 **Public**ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、のインスタンス上のすべての[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ダンプデバイスに関する情報をレポートします。  
  
```  
EXEC sp_helpdevice;  
```  
  
## <a name="see-also"></a>参照  
 [sp_addumpdevice &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_dropdevice &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースエンジン](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
