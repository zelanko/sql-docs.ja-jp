---
title: sysssislog (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdtslog90_TSQL
- sysdtslog90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssislog system table
ms.assetid: 7fa288a1-81e3-42a0-82f6-8a59019693d0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d837049f36e4f7925f8e62a18987f51235f19c14
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029609"
---
# <a name="sysssislog-transact-sql"></a>sysssislog (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パッケージ、または実行時にタスクとコンテナーによって生成されるログエントリごとに1行のレコードを格納します。 このテーブルは、のインストール[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]時に msdb データベースに作成されます。 ログ記録が別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに記録されるように構成する場合、ここで説明する形式の sysssislog テーブルが、指定されたデータベースに作成されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]パッケージが[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログプロバイダーを使用する場合に**のみ**、このテーブルにログエントリを書き込みます。  
  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|id|**int**|ログエントリの一意の識別子。|  
|イベント|**sysname**|ログ エントリを生成したイベントの名前。|  
|コンピューター|**nvarchar**|ログ エントリの生成時にパッケージが実行されていたコンピューター。|  
|operator|**nvarchar**|ログエントリを生成したパッケージを実行したユーザーのユーザー名。|  
|source|**nvarchar**|ログエントリを生成した、パッケージ内の実行可能ファイルの名前。|  
|sourceid|**UNIQUEIDENTIFIER**|ログ エントリを生成したパッケージ内の実行可能ファイルの GUID。|  
|executionid|**UNIQUEIDENTIFIER**|ログエントリを生成した実行可能ファイルの実行インスタンスの GUID。|  
|starttime|**DATETIME**|パッケージの実行が開始された時刻です。|  
|endtime|**DATETIME**|パッケージが完了した時刻です。<br /><br /> この機能は実装されていません。 Endtime 列の値は、常に starttime 列の値と同じです。|  
|datacode|**int**|コンテナーまたはタスクの実行結果を示す省略可能な整数値。|  
|databytes|**絵**|追加情報を格納しているバイト配列 (省略可能)。|  
|message|**nvarchar**|イベントの説明とイベントに関連付けられている情報。|  
  
## <a name="see-also"></a>参照  
 [SSIS&#41; ログ &#40;Integration Services](../../integration-services/performance/integration-services-ssis-logging.md)   
  
  
