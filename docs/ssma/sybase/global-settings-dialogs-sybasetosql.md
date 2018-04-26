---
title: グローバル設定 (ダイアログ ボックス) (SybaseToSQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: e11452b7-ba94-4367-a745-5ccf1764acec
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 90807867579bc47877ec662f166cc3d77caf5234
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="global-settings-dialogs--sybasetosql"></a>グローバル設定 (ダイアログ ボックス) (SybaseToSQL)
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
  
