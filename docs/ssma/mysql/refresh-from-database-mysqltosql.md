---
title: "更新からのデータベース (MySQLToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 59a6db8f-2db6-4071-9005-928a7231de92
caps.latest.revision: 4
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0e4a2afc29ff32b51a38e9df117426585e84e177
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="refresh-from-database-mysqltosql"></a>データベース (MySQLToSQL) からの更新します。
**データベースから更新** ダイアログ ボックスでは、MySQL データベースから更新するには、どのオブジェクトを選択することができます。 ダイアログ ボックス内の行が色分けされるメタデータの状態に基づいて。  
  
-   ローカルおよび MySQL のデータベースでオブジェクトのメタデータを変更した場合、行は青色です。  
  
-   SSMA ではなく、MySQL データベースにオブジェクトのメタデータが変更されている場合、行は黄色です。  
  
-   MySQL データベースではなく、行が緑オブジェクト メタデータがローカルで変更された場合。  
  
-   オブジェクトが新しい MySQL データベースの場合、行がピンク色です。  
  
オブジェクトの更新の設定を既定値を指定することができます、**プロジェクト設定** ダイアログ ボックス。 詳細については、次を参照してください。[プロジェクトの設定 & #40 です。同期 &#41;& #40 です。MySQLToSQL &#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md)  
  
アクセスする、**データベースから更新**ダイアログ ボックスで、クリックすると MySQL メタデータ エクスプ ローラー オブジェクトを右クリック**データベースから更新**です。  
  
## <a name="options"></a>オプション  
  
|||  
|-|-|  
|**項目**|**[定義]**|  
|**折りたたみ (-)**|個々 のオブジェクトを非表示にするすべてのオブジェクト グループを折りたたみます。|  
|**展開 (+)**|個々 のオブジェクトを表示するすべてのオブジェクト グループを展開します。|  
|**等しいオブジェクトを表示/非表示**|オブジェクトのメタデータが SSMA および MySQL のデータベースで同じである場合は、一覧からオブジェクトを非表示にします。|  
|**(矢印) をデータベースから更新します。**|SSMA で選択したオブジェクトのメタデータを更新することを指定するのにには、矢印ボタンを使用します。|  
|**データベースから更新を行う (X ボタン)**|SSMA で選択したオブジェクトのメタデータを更新できないことを指定するのにには、X ボタンを使用します。|  
|**凡例**|表示、**凡例** ダイアログ ボックス。 凡例には、行の色およびメタデータの状態の間のマッピングが含まれています。<br /><br />保持する、**凡例** ダイアログ ボックスの上に、**データベースから更新**ダイアログ ボックスで、**上部に表示する**チェック ボックスをオンします。|  
  

