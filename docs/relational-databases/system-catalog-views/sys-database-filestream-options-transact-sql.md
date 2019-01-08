---
title: sys.database_filestream_options (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_filestream_options
- sys.database_filestream_options_TSQL
- database_filestream_options_TSQL
- sys.database_filestream_options
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_filestream_options catalog view
ms.assetid: 3383c607-0bbc-456a-ab37-7230f4cbf0e9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3038b27084dce6a84436e658c66b77dc61ead49e
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52543022"
---
# <a name="sysdatabasefilestreamoptions-transact-sql"></a>sys.database_filestream_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  FileTable 内の有効化された FILESTREAM データに対する非トランザクション アクセスのレベルに関する情報を表示します。 SQL Server インスタンス内にあるデータベースごとに 1 行のデータを格納します。  
  
 FileTables について詳しくは、「[FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)」をご覧ください。  
  
  
|[列]|型|説明|  
|------------|----------|-----------------|  
|**database_id**|**int**|データベースの ID です。 この値は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内で一意になっています。|  
|**directory_name**|**nvarchar (255)**|すべての FileTable 名前空間のデータベース レベルのディレクトリです。|  
|**non_transacted_access**|**tinyint**|有効化されている FILESTREAM データへの非トランザクション アクセスのレベルです。 アクセスのレベルの NON_TRANSACTED_ACCESS オプションで設定されます、 **CREATE DATABASE**または**ALTER DATABASE**ステートメント。<br /><br /> この設定は、次のいずれかの値になります。<br /><br /> 0 - 有効になっていません。 これが既定値です。 このレベルは、値を提供することによって設定**OFF**の**NON_TRANSACTED_ACCESS**オプション。<br /><br /> 1-読み取り専用アクセス。 このレベルは、値を提供することによって設定**READ_ONLY**の**NON_TRANSACTED_ACCESS**オプション。<br /><br /> 3-フル アクセス。 このレベルは、値を提供することによって設定**完全**の**NON_TRANSACTED_ACCESS**オプション。<br /><br /> 5 - READONLY に移行中。<br /><br /> 6 - OFF に移行中|  
|**non_transacted_access_desc**|**nvarchar(60)**|Non_transacted_access で識別される非トランザクション アクセスのレベルの説明です。<br /><br /> この設定は、次のいずれかの値になります。<br /><br /> NONE - これは既定値です。<br /><br /> READ_ONLY<br /><br /> FULL<br /><br /> IN_TRANSITION_TO_READ_ONLY<br /><br /> IN_TRANSITION_TO_OFF|  
  
## <a name="see-also"></a>参照  
 [FileTable の前提条件の有効化](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
  
