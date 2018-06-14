---
title: 更新からのデータベース (DB2ToSQL) |Microsoft ドキュメント
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 613a8368-b372-443f-8252-fb6dc31a003d
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: f61bbf015c9c4a1dc0a650aa2299e763b00e7e62
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34775328"
---
# <a name="refresh-from-database-db2tosql"></a>データベース (DB2ToSQL) からの更新します。
**データベースから更新** ダイアログ ボックスを使用して、DB2 データベースから更新するには、どのオブジェクトを選択できます。 ダイアログ ボックス内の行が色分けされるメタデータの状態に基づいて。  
  
-   ローカルおよび DB2 データベース内でオブジェクトのメタデータを変更した場合、行は青色です。  
  
-   SSMA ではなく DB2 データベースにオブジェクトのメタデータが変更されている場合、行は黄色です。  
  
-   オブジェクトのメタデータがローカルで変更されていて、DB2 データベースではなく、行が緑場合。  
  
-   オブジェクトは、DB2 データベースに新しい行はピンクであります。  
  
オブジェクトの更新の設定を既定値を指定することができます、**プロジェクト設定** ダイアログ ボックス。 詳細については、次を参照してください。[プロジェクト設定&#40;同期&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md)です。  
  
アクセスする、**データベースから更新**DB2 メタデータ エクスプ ローラー内のオブジェクトを右クリックしてダイアログ ボックスで、**データベースから更新**です。  
  
## <a name="options"></a>および  
**折りたたみ (-)**  
個々 のオブジェクトを非表示にするすべてのオブジェクト グループを折りたたみます。  
  
**展開 (+)**  
個々 のオブジェクトを表示するすべてのオブジェクト グループを展開します。  
  
**等しいオブジェクトを表示/非表示**  
オブジェクトのメタデータが SSMA および DB2 データベースで同じである場合は、一覧からオブジェクトを非表示にします。  
  
**(矢印) をデータベースから更新します。**  
SSMA で選択したオブジェクトのメタデータを更新することを指定するのにには、矢印ボタンを使用します。  
  
**データベースから更新を行う (X ボタン)**  
SSMA で選択したオブジェクトのメタデータを更新できないことを指定するのにには、X ボタンを使用します。  
  
**凡例**  
表示、**凡例** ダイアログ ボックス。 凡例には、行の色およびメタデータの状態の間のマッピングが含まれています。  
  
保持する、**凡例** ダイアログ ボックスの上に、**データベースから更新**ダイアログ ボックスで、**上部に表示する**チェック ボックスをオンします。  
  
