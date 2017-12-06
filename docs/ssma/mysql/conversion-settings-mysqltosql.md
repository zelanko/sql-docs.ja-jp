---
title: "変換の設定 (MySQLToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-mysql
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
ms.assetid: f551cf6e-1575-4206-9cca-975b5b43a6b8
caps.latest.revision: "10"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 58dc331830f70cee8389a38a425adb1daceb3e27
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="conversion-settings-mysqltosql"></a>変換の設定 (MySQLToSQL)
**'設定'**  タブでは、ユーザーをノード レベルの設定を設定します。 タブは、次のメタベース ノードで使用可能なになります。  
  
-   データベース ノード  
  
-   関数のカテゴリ  
  
-   関数ノード  
  
-   テーブルのカテゴリ  
  
-   テーブルのノード  
  
## <a name="specifications"></a>仕様:  
**設定**タブには、次の 2 つのユーザー設定 viz。  
  
1.  関数の変換  
  
2.  テーブルの変換  
  
これらの設定は、メタベースのノードの種類に基づいて、使用可能なであるは。 たとえば、設定関数の変換は関連は利用できませんテーブル ノード  
  
> [!NOTE]  
> -   ユーザーによって行われた変更は、プロジェクト ワークスペースで、別の基本設定ファイルとして保存されます。  
> -   このファイルの拡張子はでは**ccprefs**です。  
  
1.  **関数の変換の設定:**  
  
    1.  このタブには**'関数の変換を Force'**オプション。 オプションは、次の 4 つの値のいずれかを持つことができます。  
  
        -   [継承] プロジェクト設定に従って変換します。  
  
        -   常に、関数に変換します。  
  
        -   常に、プロシージャに変換します。  
  
        -   プロジェクトの設定に応じて変換します。  
  
    2.  設定に基づき、関数またはストアド プロシージャのいずれかの関数が変換されます。  
  
    3.  ユーザーによる設定をクリックすると、カスケード設定ファイルに保存されます**適用**ボタンをクリックします。  
  
2.  **テーブルの変換の設定:**  
  
    1.  このタブには**'抑制 ROWID 補助列の生成'**オプション。 オプションは、次の 4 つの値のいずれかを持つことができます。  
  
        -   [継承] プロジェクト設定に従って変換します。  
  
        -   可  
  
        -   不可  
  
        -   プロジェクトの設定に応じて変換します。  
  
    2.  場合**'Yes'**、この設定は、ROWID 補助型の列の作成対象になるテーブルの作成を禁止します。  
  
    3.  ユーザーが行った設定をクリックするカスケード設定ファイルに保存されます**適用**ボタンをクリックします。  
  
## <a name="see-also"></a>参照  
[プロジェクトの設定 (変換) (MySQL to SQL)](http://msdn.microsoft.com/en-us/7ad5fe44-6445-4ba8-a457-5af792631f11)  
  
