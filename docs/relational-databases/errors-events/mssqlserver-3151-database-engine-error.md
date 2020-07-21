---
title: MSSQLSERVER_3151 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d0d4c51bd7f4e1eca3bf57fbcfa89aec93357fb0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723741"
---
# <a name="mssqlserver_3151"></a>MSSQLSERVER_3151
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|3151|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|LDDB_MASTER_LOAD_FAILED|  
|メッセージ テキスト|master データベースを復元できませんでした。 SQL Server をシャットダウンしています。 エラー ログを確認し、master データベースを再構築してください。 master データベースを再構築する方法の詳細については、SQL Server オンライン ブックを参照してください。|  
  
## <a name="explanation"></a>説明  
これは一般エラー メッセージであり、**master** データベースに関するさまざまな問題を示しています。  
  
## <a name="user-action"></a>ユーザーの操作  
詳細については、エラー ログを確認してください。 使用可能な **master** データベースを作成するには、REBUILDDATABASE オプションを使用して Setup.exe を実行します。 詳細については、SQL Server オンライン ブックの「方法:コマンド プロンプトからの SQL Server のインストール」を参照してください。  
  
