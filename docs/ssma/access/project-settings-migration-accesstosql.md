---
title: プロジェクトの設定 (移行) (AccessToSQL) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-access
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
ms.openlocfilehash: 3fe26ecc9d250982206121d33b35ee5c975e376f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="project-settings-migration-accesstosql"></a>プロジェクトの設定 (移行) (AccessToSQL)
移行プロジェクトの設定では、データに移行する方法を構成できます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。  
  
移行ペインがで使用できる、**プロジェクト設定**と**プロジェクト設定の既定の** ダイアログ ボックス。  
  
-   使用して、**プロジェクト設定**ダイアログ ボックスを現在のプロジェクトの構成オプションを設定します。 移行の設定にアクセスする、**ツール**メニューの [**プロジェクト設定**、] をクリックして**全般**クリックして、左側のウィンドウの下部にある**移行**です。  
  
-   使用して、**プロジェクト設定の既定の**ダイアログ ボックスをすべてのプロジェクトの構成オプションを設定します。 移行の設定にアクセスする、**ツール**メニューの **プロジェクト設定の既定の**、プロジェクトの種類を選択**移行のターゲット バージョン**コンボ ボックスの設定にアクセスをクリックする**全般**クリックして、左側のウィンドウの下部にある**移行**です。  
  
## <a name="options"></a>オプション  
**CHECK 制約**  
テーブルにデータを追加する場合、SSMA が制約をチェックするかどうかを指定します。  
  
-   **既定のモード**: False  
  
-   **オプティミスティック モード**: True  
  
-   **Full モード**: False  
  
**[トリガーを起動する]**  
データを追加する場合に、SSMA が挿入トリガーを起動するかどうかを示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]テーブル。  
  
-   **既定のモード**: False  
  
-   **オプティミスティック モード**: True  
  
-   **Full モード**: False  
  
**[ID を保持する]**  
SSMA では、データを追加する場合に、アクセスの id 値が保持されるかどうかを示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 この値が False の場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]id 値を割り当てます。  
  
-   **既定のモード**: True  
  
-   **オプティミスティック モード**: True  
  
-   **Full モード**: False  
  
**[NULL を保持する]**  
SSMA では、データを追加する場合に、ソース データ内の null 値が保持されるかどうかを示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]で指定されている既定値に関係なく、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
-   **既定のモード**: True  
  
-   **オプティミスティック モード**: False  
  
-   **Full モード**: True  
  
**テーブル ロック**  
SSMA がデータの移行中のテーブルにデータを追加する場合に、テーブルをロックするかどうかを指定します。 値が False の場合は、SSMA は、行ロックを使用します。  
  
-   **既定のモード**: True  
  
-   **オプティミスティック モード**: True  
  
-   **Full モード**: True  
  
**サポートされていない日付を置き換えます**  
SSMA はできるだけ早くより前のアクセスの日付を修正する必要があるかどうかを示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]datetime の日付 (1753 年 1 月 01日)。  
  
-   現在の日付値を保持する次のように選択します。**何もしない**です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] datetime 列には、01 1753 年 1 月より前に、の日付を受け入れません。 古い日付を使用する場合は、datetime 値を文字の値に変換する必要があります。  
  
-   01 1753 年 1 月より前に、の日付を NULL に変換する選択**NULL 置き換えます**です。  
  
-   サポートされている日付の 01 1753 年 1 月より前に、の日付を置き換えるには選択**でサポートされる日付に最も近い置き換えます**です。 既定では最も近い値を選択した場合、サポートされている日付は 01 1753 年 1 月として選択されます。  
  
**バッチ サイズ**  
バッチ サイズがデータの移行時に使用します。 各バッチの後にトランザクションが記録されます。 既定では、すべてのスキームのバッチ サイズは 10000 です。  
  
## <a name="see-also"></a>参照  
[ユーザー インターフェイス Reference(Access)](http://msdn.microsoft.com/en-us/af24c303-4a41-449b-9c86-d6558a97e839)  
  
