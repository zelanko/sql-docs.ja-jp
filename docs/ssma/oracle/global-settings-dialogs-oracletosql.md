---
title: "グローバル設定 (ダイアログ ボックス) (OracleToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43989355-cebf-4d8b-ba3d-fa8546e70230
caps.latest.revision: "3"
author: Shamikg
ms.author: Shamikg
manager: v-pelars
ms.workload: Inactive
ms.openlocfilehash: 9e80e0b3e2fe055d6fa960e8b830cbe41bbdca90
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="global-settings-dialogs--oracletosql"></a>グローバル設定 (ダイアログ ボックス) (OracleToSQL)
ダイアログ ページを使用して、**グローバル設定**ダイアログ ボックスを既定のユーザー アクションと SSMA に対する警告の設定を指定します。  
  
設定にアクセスする、ダイアログで、**ツール**メニューの [**グローバル設定**、] をクリックして**GUI**クリックし、左側のウィンドウの下部にある**ダイアログ**です。  
  
## <a name="options"></a>オプション  
**オブジェクトを上書きする前に警告する します。**  
SSMA では、オブジェクトを SQL Server に変換して、ときに一部のオブジェクトが、プロジェクトの SQL Server のメタデータに存在既に可能性があります。 これらのオブジェクトは既に変換されている可能性があります、か、オブジェクトは、オブジェクトに変換しようとすると、ターゲット スキーマ内に同じ名前を持つ単純に可能性があります。  
  
指定するかどうか SSMA ように求めるメッセージが重複しているオブジェクトの定義を上書きするためには、このオプションを使用します。  
  
-   選択した場合**True**SSMA は、重複するオブジェクトを検出すると、警告ダイアログ ボックスに表示されます。 このダイアログ ボックスでは、個々 のオブジェクトまたはすべての重複するオブジェクトを上書きするか、個々 のオブジェクトまたはすべての重複するオブジェクトをスキップするを指定できます。  
  
-   選択した場合**False**、**オブジェクトの既定の動作を上書きする**既定のアクションを指定するオプションが表示されます。  
  
**オブジェクトの上書きの既定のアクション**  
選択した場合、このオプションが表示されます**False**の**オブジェクトを上書きする前に警告する**オプション。  
  
既定のオブジェクトの上書き動作を指定するのにには、このオプションを使用します。  
  
-   選択した場合**True**SSMA は、同じ名前を持ち、変換するオブジェクトと同じターゲット スキーマでは、SQL Server プロジェクトのメタデータ内のオブジェクトを自動的に上書きします。  
  
-   選択した場合**False**SSMA では、オブジェクト メタデータの変換中に上書きされません。  
  
