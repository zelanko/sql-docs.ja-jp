---
title: グローバル設定 (ダイアログ ボックス) (DB2ToSQL) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
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
ms.assetid: 360e01bb-6347-4e2b-acda-0daa161ed33b
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ae164bb796089542d8c4b3b6fe78b0f82a21cb3b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="global-settings-dialogs-db2tosql"></a>グローバル設定 (ダイアログ ボックス) (DB2ToSQL)
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
  
