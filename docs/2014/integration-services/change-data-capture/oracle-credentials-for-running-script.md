---
title: スクリプトを実行するための Oracle 資格情報 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ca3f76c49b950f6830c4d60f011bbdb158055179
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52796094"
---
# <a name="oracle-credentials-for-running-script"></a>Oracle Credentials for Running Script
  Oracle CDC デザイナー コンソールから Oracle の補足ログ スクリプトを実行するために、スクリプトを実行する Oracle ユーザーの資格情報の入力が求められます。 このスクリプトを実行するには、キャプチャするすべてのテーブルに対する ALTER TABLE 権限と、DBA_LOG_GROUPS ビューに対する SELECT 権限が Oracle ユーザーに必要です。  
  
## <a name="task-list"></a>タスク一覧  
 このダイアログ ボックスでは次の情報を入力します。  
  
 **[認証]**  
  
 次のいずれかを選択します。  
  
-   **Windows 認証**:現在の Windows ドメイン資格情報を使用する場合に選択します。 このオプションは、Oracle データベースが Windows 認証と連動するように構成されている場合にのみ使用できます。  
  
-   **Oracle 認証**:このオプションを選択する場合は入力、**ユーザー名**と**パスワード**ソース Oracle データベースに接続しているユーザー。  
  
## <a name="see-also"></a>参照  
 [CDC インスタンスを管理する方法](manage-a-cdc-instance.md)   
 [補足ログ スクリプトの確認および生成](review-and-generate-supplemental-logging-scripts.md)  
  
  
