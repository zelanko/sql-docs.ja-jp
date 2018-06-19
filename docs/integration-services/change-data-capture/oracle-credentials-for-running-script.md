---
title: スクリプトを実行するための Oracle 資格情報 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4dab2281504a563fdc257ea398ae168ce1af2fd1
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35407344"
---
# <a name="oracle-credentials-for-running-script"></a>Oracle Credentials for Running Script
  Oracle CDC デザイナー コンソールから Oracle の補足ログ スクリプトを実行するために、スクリプトを実行する Oracle ユーザーの資格情報の入力が求められます。 このスクリプトを実行するには、キャプチャするすべてのテーブルに対する ALTER TABLE 権限と、DBA_LOG_GROUPS ビューに対する SELECT 権限が Oracle ユーザーに必要です。  
  
## <a name="task-list"></a>タスク一覧  
 このダイアログ ボックスでは次の情報を入力します。  
  
 **[認証]**  
  
 次のいずれかを選択します。  
  
-   **[Windows 認証]**: 現在の Windows ドメイン資格情報を使用する場合に選択します。 このオプションは、Oracle データベースが Windows 認証と連動するように構成されている場合にのみ使用できます。  
  
-   **[Oracle 認証]**: このオプションを選択する場合、接続先のソース Oracle データベースでのユーザーの **[ユーザー名]** と **[パスワード]** を入力する必要があります。  
  
## <a name="see-also"></a>参照  
 [CDC インスタンスを管理する方法](../../integration-services/change-data-capture/how-to-manage-a-cdc-instance.md)   
 [補足ログ スクリプトの確認および生成](../../integration-services/change-data-capture/review-and-generate-supplemental-logging-scripts.md)  
  
  
