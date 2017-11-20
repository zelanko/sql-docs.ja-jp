---
title: "Oracle の補足ログ スクリプト |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e6ee618-b89b-46c7-92ad-4fc5ef7b777a
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 16e3c1b59550236eaa1716d7251e55c0cee6b919
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="oracle-supplemental-logging-script"></a>Oracle の補足ログ スクリプト
  このダイアログ ボックスには、Oracle の補足ログ スクリプトが表示されます。  
  
 CDC インスタンスを使用に備えて準備すると、CDC デザイナーにより、キャプチャするテーブル用の補足ログを設定する Oracle SQL スクリプトが作成されます。 補足ログ スクリプトは Oracle に対し、特定のテーブルが更新された場合、トランザクション ログに書き込む変更レコードに、変更された列だけでなく、対象のすべての列のデータを含める必要があることを伝えます。  
  
 組織の Oracle DBA ポリシーによっては、補足ログ スクリプトを実行するために、Oracle DBA による確認と承認が必要な場合があります。  
  
## <a name="options"></a>オプション  
 スクリプトの実行方法について使用可能なオプションを次に示します。  
  
 **[スクリプトの実行]**  
 CDC インスタンスに定義されているテーブルで補足ログ スクリプトを実行します。 このスクリプトを実行するには、キャプチャするすべてのテーブルに対する ALTER TABLE 権限と、DBA_LOG_GROUPS ビューに対する SELECT 権限が Oracle ユーザーに必要です。 さらに、必要な権限と共に使用する Oracle データベースの資格情報が Oracle ユーザーに必要です。 プログラムに Oracle 資格情報を要求させ、スクリプトを実行させることができます。  
  
 **[名前を付けて保存]**  
 スクリプトをテキスト ファイルに保存します。 このオプションは、Oracle データベース管理者 (DBA) が補足ログ スクリプトを調べて実行する必要がある場合に使用されます。ユーザーはスクリプトをテキスト ファイルに保存し、そのテキスト ファイルを後で Oracle DBA に電子メールまたはその他の方法で送信して実行してもらうことができます (SQL*Plus Oracle ユーティリティまたは Oracle データベースでスクリプトを実行するためのその他のツールを使用)。  
  
 **[コピー]**  
 スクリプトをクリップボードにコピーします。 Oracle 管理者 (DBA) が補足ログ スクリプトを調べて実行する必要がある場合は、必要な場所にスクリプトを貼り付けることができます。  
  
## <a name="see-also"></a>参照  
 [CDC インスタンスを管理する方法](../../integration-services/change-data-capture/how-to-manage-a-cdc-instance.md)   
 [CDC インスタンスを管理します。](../../integration-services/change-data-capture/manage-a-cdc-instance.md)  
  
  

