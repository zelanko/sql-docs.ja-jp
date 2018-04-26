---
title: 型のマッピング (OracleToSQL) は編集 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7078b4ed-c779-4bf3-8db8-f9dcb3edd50f
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: c089d4f05ff66ea01d74f43538b886b82066f4e1
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="edit-type-mapping-oracletosql"></a>型のマッピング (OracleToSQL) の編集します。
**型マッピングの編集** ダイアログ ボックスでは、ソースと変換先のデータベース オブジェクト間の種類をマップする方法を指定することができます。  
  
複数の場所でこのダイアログ ボックスを表示できます。  
  
-   ソース データベースまたはデータベース オブジェクトを選択すると、**型マッピング**タブは、メタデータ エクスプ ローラーの右側に表示されます。 をクリックして**追加**を新しい型マッピングを追加する**編集**を既存の型マッピングを変更します。  
  
-   **ツール**メニューの **プロジェクト設定**または**プロジェクト設定の既定の**します。 結果として得られる ダイアログ ボックスで選択**型マッピング**です。 をクリックして**追加**を新しい型マッピングを追加する**編集**を既存の型マッピングを変更します。  
  
テーブルに固有の型マッピングは、データベースをオーバーライドし、プロジェクトの種類のマッピング。 データベース固有のマッピングは、project のマッピングをオーバーライドします。  
  
## <a name="options"></a>オプション  
**ソースの種類**  
マップするソースのデータ型を選択して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
次のフィールドが表示されます、データ型が可変長の場合は、**ソースの種類**:  
  
**From**  
このマッピングの最小の長さを指定します。 たとえば、 **nchar**データ型を開始位置として、範囲のこのマッピングであることを指定する 10」と入力することができます**nchar(10)** です。  
  
**変換先**  
このマッピングの最大長を指定します。 たとえば、 **nchar**データ型で終わる範囲のこのマッピングであることを指定する 20」と入力することができます**nchar (20) 型**です。  
  
**ターゲットの種類**  
選択、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ソースのデータ型がマップされているデータ型。 SSMA がテーブルまたはストアド プロシージャを作成すると[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ソースのデータ型は、このデータ型に変更されます。  
  
次のフィールドを下に表示されます、データ型が可変長の場合は、**ターゲット型**:  
  
**Replace with**  
このマッピングのターゲットの長さを指定します。 たとえば、 **nvarchar**データ型に指定したソースのデータ型をマップする必要がありますを指定する 20」と入力することができます**nvarchar (20)** です。  
  
