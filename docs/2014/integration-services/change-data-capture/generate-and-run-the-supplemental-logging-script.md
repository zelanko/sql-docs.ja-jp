---
title: 補足ログ スクリプトの生成および実行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- supLog
ms.assetid: 6e940d93-12c6-4cda-9333-5489b245f0e4
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 45948070acddfd919a30b57fc0bebb88bdedf2aa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37254674"
---
# <a name="generate-and-run-the-supplemental-logging-script"></a>補足ログ スクリプトの生成および実行
  補足ログを設定する Oracle ソース データベースでスクリプトを実行するには、[変更をキャプチャするためのテーブルの設定] ページを使用します。  
  
 **補足ログ スクリプトを実行するには**  
  
 **[スクリプトの実行]** をクリックして、CDC インスタンスに定義されているテーブルで補足ログ スクリプトを実行します。 このスクリプトは、キャプチャされるテーブルに UPDATE 操作のログを記録するときに、必要なすべての列をトランザクション ログに書き込むように Oracle データベースに対して指示します。 通常、このスクリプトは Oracle システム管理者によって検査されて実行されます。  
  
 SQL*Plus を使用してスクリプトを手動で実行することもできます。  
  
 **スクリプトを手動で実行するには**  
  
 **[コピー]** をクリックしてスクリプトをクリップボードに貼り付けます。 SQL*Plus を開き、Oracle ソース データベースのディレクトリに移動します。 SQL\*Plus にスクリプトを貼り付けて実行します。  
  
 補足ログ スクリプトをテキスト ファイルで保存するには、 **[名前を付けて保存]** をクリックし、ファイルを保存する場所を参照します。 ファイルに名前を付け、 **[保存]** をクリックしてファイルを保存します。  
  
 **[次へ]** をクリックして「 [Generate Mirror Tables and CDC Capture Instances](generate-mirror-tables-and-cdc-capture-instances.md)」に進みます。  
  
## <a name="see-also"></a>参照  
 [SQL Server 変更データベース インスタンスを作成する方法](how-to-create-the-sql-server-change-database-instance.md)   
 [補足ログ スクリプトの確認および生成](review-and-generate-supplemental-logging-scripts.md)  
  
  
