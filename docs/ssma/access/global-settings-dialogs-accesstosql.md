---
title: "グローバル設定 (ダイアログ ボックス) (AccessToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 6c2204f2-d49e-49ba-9c0f-f14cf07fa561
caps.latest.revision: "3"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 781df720701bfebc06faa43e782ae98167bd98b5
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="global-settings-dialogs-accesstosql"></a>グローバル設定 (ダイアログ ボックス) (AccessToSQL)
ダイアログ ページを使用して、**グローバル設定**ダイアログ ボックスを既定のユーザー アクションと SSMA に対する警告の設定を指定します。  
  
設定にアクセスする、ダイアログで、**ツール**メニューの [**グローバル設定**、] をクリックして**GUI**クリックし、左側のウィンドウの下部にある**ダイアログ**です。  
  
## <a name="options"></a>オプション  
**起動時に移行ウィザードを表示します。**  
SSMA for Access で有効または無効にするオプションがある**移行ウィザード**SSMA アプリケーションの起動時にします。 このオプションは、既定では**True**です。  
  
-   オプションが に設定されている場合**True**、移行ウィザードのダイアログが最初に表示されると、Access アプリケーションの SSMA を開いたときです。  
  
-   オプションが に設定されている場合**False**、移行ウィザードが表示されずから手動でアクセスする必要が、**ファイル** メニューの 必要な場合です。  
  
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
  
