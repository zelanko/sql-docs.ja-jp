---
title: MSSQLSERVER_3431 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3431 (Database Engine error)
ms.assetid: 9541217f-e5c6-4a12-a19a-006058f1d3f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e154abe34543127427aaad0918649342dedd3fa1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723505"
---
# <a name="mssqlserver_3431"></a>MSSQLSERVER_3431
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|3431|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|UNRESOLVED_XACT|  
|メッセージ テキスト|トランザクションの結果を解決できないので、データベース '%.*ls' (データベース ID %d) を復旧できませんでした。 Microsoft 分散トランザクション コーディネーター (MS DTC) のトランザクションは準備されていましたが、MS DTC では解決策を決定できませんでした。 解決するには、MS DTC の修正、完全バックアップからの復元、またはデータベースの修復のいずれかを実行してください。|  
  
## <a name="explanation"></a>説明  
データベースをシャットダウンしたときに、[!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) を使用する分散トランザクションの 1 つ以上が完了しませんでした。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、MS DTC からの詳細な情報がないとトランザクションの完了やロールバックを行うことができないので、このデータベースの復旧は失敗します。  
  
## <a name="user-action"></a>ユーザーの操作  
このデータベースを復旧するには、まず MS DTC の問題を解決する必要があります。 MS DTC の問題を調査するため、Windows イベント ログを確認します。 MS DTC の問題を解決してデータベースを復旧できない場合は、データベースのバックアップを復元します。  
  
