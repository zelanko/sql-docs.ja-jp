---
title: "更新からのデータベース (OracleToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84492f44-c368-4c75-954d-7307a2d2bbc0
caps.latest.revision: 4
author: sabotta
ms.author: carlasab
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 536fa920910c56698be8b161f59294f555747917
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="refresh-from-database-oracletosql"></a>データベース (OracleToSQL) からの更新します。
**データベースから更新** ダイアログ ボックスでは、Oracle データベースから更新するには、どのオブジェクトを選択することができます。 ダイアログ ボックス内の行が色分けされるメタデータの状態に基づいて。  
  
-   ローカルおよび Oracle データベースでオブジェクトのメタデータを変更した場合、行は青色です。  
  
-   SSMA ではなく、Oracle データベースでオブジェクトのメタデータが変更されている場合、行は黄色です。  
  
-   オブジェクトのメタデータがローカルで変更されていて、Oracle データベースではなく、行が緑場合。  
  
-   オブジェクトが、Oracle データベースで新しい場合、行がピンク色です。  
  
オブジェクトの更新の設定を既定値を指定することができます、**プロジェクト設定** ダイアログ ボックス。 詳細については、次を参照してください。[プロジェクトの設定 & #40 です。同期 &#41;&#40; OracleToSQL &#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md).  
  
アクセスする、**データベースから更新**ダイアログ ボックスで、クリックすると Oracle メタデータ エクスプ ローラー オブジェクトを右クリック**データベースから更新**です。  
  
## <a name="options"></a>オプション  
**折りたたみ (-)**  
個々 のオブジェクトを非表示にするすべてのオブジェクト グループを折りたたみます。  
  
**展開 (+)**  
個々 のオブジェクトを表示するすべてのオブジェクト グループを展開します。  
  
**等しいオブジェクトを表示/非表示**  
オブジェクトのメタデータが SSMA と Oracle データベースで同じである場合は、一覧からオブジェクトを非表示にします。  
  
**(矢印) をデータベースから更新します。**  
SSMA で選択したオブジェクトのメタデータを更新することを指定するのにには、矢印ボタンを使用します。  
  
**データベースから更新を行う (X ボタン)**  
SSMA で選択したオブジェクトのメタデータを更新できないことを指定するのにには、X ボタンを使用します。  
  
**凡例**  
表示、**凡例** ダイアログ ボックス。 凡例には、行の色およびメタデータの状態の間のマッピングが含まれています。  
  
保持する、**凡例** ダイアログ ボックスの上に、**データベースから更新**ダイアログ ボックスで、**上部に表示する**チェック ボックスをオンします。  
  

