---
title: プロジェクトの設定 (移行) (AccessToSQL) |Microsoft Docs
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
helpviewer_keywords:
- Migration settings
- Project Settings dialog box, Migration
ms.assetid: 4caebc9c-8680-4b99-a8fa-89c43161c95d
caps.latest.revision: 14
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 10346770784c94fe18357b5717e60f7e3f88a8c7
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "40395336"
---
# <a name="project-settings-migration-accesstosql"></a>プロジェクトの設定 (移行) (AccessToSQL)
移行プロジェクトの設定では、データを移行する方法を構成できます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure です。  
  
移行のウィンドウが表示されます、**プロジェクト設定**と**プロジェクト設定の既定の** ダイアログ ボックス。  
  
-   使用して、**プロジェクト設定**ダイアログ ボックスを現在のプロジェクトの構成オプションを設定します。 移行の設定にアクセスする、**ツール**メニューの [**プロジェクト設定**、] をクリックして**全般**クリックし、左側のウィンドウの下部にある**移行**します。  
  
-   使用して、**プロジェクト設定の既定の**ダイアログ ボックスをすべてのプロジェクトの構成オプションを設定します。 移行の設定にアクセスする、**ツール**メニューの [**プロジェクト設定の既定の**、プロジェクトの種類を選択します**移行ターゲット バージョン**コンボ ボックスをします。設定にアクセスします] をクリックする**全般**クリックし、左側のウィンドウの下部にある**移行**します。  
  
## <a name="options"></a>および  
**CHECK 制約**  
テーブルにデータを追加する場合、SSMA が制約をチェックするかどうかを指定します。  
  
-   **既定のモード**: False  
  
-   **オプティミスティック モード**: True  
  
-   **フル モード**: False  
  
**[トリガーを起動する]**  
データを追加するときに、SSMA が挿入トリガーを起動するかどうかを指定します。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。  
  
-   **既定のモード**: False  
  
-   **オプティミスティック モード**: True  
  
-   **フル モード**: False  
  
**[ID を保持する]**  
SSMA では、データを追加する場合に、アクセス id の値が保持されるかどうかを指定します。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 この値が False の場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]id 値を割り当てます。  
  
-   **既定のモード**: True  
  
-   **オプティミスティック モード**: True  
  
-   **フル モード**: False  
  
**[NULL を保持する]**  
SSMA では、データを追加する場合に、ソース データ内の null 値が保持されるかどうかを指定します。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で指定されている既定値に関係なく、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
-   **既定のモード**: True  
  
-   **オプティミスティック モード**: False  
  
-   **フル モード**: True  
  
**テーブル ロック**  
データ移行中にデータをテーブルに追加する場合、SSMA でテーブルをロックするかどうかを指定します。 値が False の場合は、SSMA は、行ロックを使用します。  
  
-   **既定のモード**: True  
  
-   **オプティミスティック モード**: True  
  
-   **フル モード**: True  
  
**サポートされていない日付を置き換えます**  
SSMA は、最も古いより前のアクセスの日付を修正する必要があるかどうかを指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datetime の日付 (1753 年 1 月 1)。  
  
-   現在の日付値を保持する次のように選択します。**何**します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] datetime 列 01 1753 年 1 月より前に、の日付は受け入れません。 古い日付を使用する場合は、datetime 値を文字の値に変換する必要があります。  
  
-   01 1753 年 1 月より前に、の日付を NULL に変換する選択**を NULL**します。  
  
-   サポートされている日付を 01 1753 年 1 月より前に、の日付を置き換えるには選択**サポートされている日付に最も近い置き換えます**します。 最も近い既定で、この値を選択した場合、01 1753 年 1 月としてサポートされている日付が選択されます。  
  
**バッチ サイズ**  
データ移行中に使用されるバッチ サイズ。 各バッチの後にトランザクションが記録されます。 既定では、すべての構成のバッチ サイズは 10000 です。  
  
## <a name="see-also"></a>参照  
[ユーザー インターフェイスの Reference(Access)](http://msdn.microsoft.com/en-us/af24c303-4a41-449b-9c86-d6558a97e839)  
  
