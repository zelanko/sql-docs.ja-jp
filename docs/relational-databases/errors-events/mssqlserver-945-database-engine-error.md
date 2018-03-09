---
title: MSSQLSERVER_945 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7b5306ced8c5112d179060b574442849e4b9457f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver945"></a>MSSQLSERVER_945
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|945|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DB_IS_SHUTDOWN|  
|メッセージ テキスト|ファイルにアクセスできないか、メモリまたはディスク領域が不足しているので、データベース '%.*ls' を開けません。  詳細については、SQL Server エラー ログを確認してください。|  
  
## <a name="explanation"></a>説明  
ファイルなどのリソースが存在しないため、データベースにアクセスできませんでした。  
  
## <a name="user-action"></a>ユーザーの操作  
エラー ログを参照し、メモリ、ディスク領域、または権限のエラーに関する追加情報を確認してください。 影響を受けたデータベースの .mdf ファイルと .ndf ファイルの場所を確認し、[!INCLUDE[ssDE](../../includes/ssde-md.md)]で使用するアカウントにこれらのファイルへのアクセス権が与えられていることを確認します。 問題を解決した後、データベースを再起動します。この操作を行うには、ALTER DATABASE を使用して、データベースを ONLINE に設定します。  
  
