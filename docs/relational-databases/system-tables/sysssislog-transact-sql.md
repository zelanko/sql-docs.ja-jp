---
title: sysssislog (TRANSACT-SQL) |Microsoft Docs
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
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 536a4b6c89b3d2c407d234ad0e5821782425b6b4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56016953"
---
# <a name="sysssislog-transact-sql"></a>sysssislog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パッケージやパッケージのタスク、およびコンテナーによって実行時に生成される各ログ エントリに対して、1 行のデータを格納します。 このテーブルは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] をインストールするときに msdb データベースに作成されます。 ログ記録が別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに記録されるように構成する場合、ここで説明する形式の sysssislog テーブルが、指定されたデータベースに作成されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] このテーブルにログ エントリを書き込みます**のみ**パッケージを使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログ プロバイダー。  
  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|id|**int**|ログ エントリの一意識別子。|  
|イベント|**sysname**|ログ エントリを生成したイベントの名前。|  
|computer|**nvarchar**|ログ エントリの生成時にパッケージが実行されていたコンピューター。|  
|演算子 (operator)|**nvarchar**|ログ エントリを生成したパッケージを実行したユーザーの名前。|  
|source|**nvarchar**|ログ エントリを生成したパッケージ内の実行可能ファイルの名前。|  
|sourceid|**uniqueidentifier**|ログ エントリを生成したパッケージ内の実行可能ファイルの GUID。|  
|executionid|**uniqueidentifier**|ログ エントリを生成した実行可能ファイルの実行インスタンスの GUID。|  
|starttime|**datetime**|パッケージの実行が開始された時刻。|  
|endtime|**datetime**|パッケージが完了した時刻。<br /><br /> この機能は実装されていません。 [endtime] 列の値は、[starttime] 列の値と常に同じになります。|  
|datacode|**int**|コンテナーまたはタスクの実行結果を通常示す整数値 (省略可能)。|  
|databytes|**image**|追加情報を格納しているバイト配列 (省略可能)。|  
|message|**nvarchar**|イベントおよびイベントに関連する情報の説明。|  
  
## <a name="see-also"></a>参照  
 [Integration Services &#40;SSIS&#41; のログ記録](../../integration-services/performance/integration-services-ssis-logging.md)   
  
  
