---
title: ドライバセットアップ DLL |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], driver setup DLL
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: 49bab021-81fa-402e-b7a4-a5214f1fadc4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a0a2878591c92fe0b2070a295d9dc622c245c17e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306423"
---
# <a name="driver-setup-dll"></a>ドライバーのセットアップ DLL
> [!NOTE]  
>  WINDOWS XP および Windows Server 2003 以降では、ODBC が Windows のオペレーション システムに含まれています。 ODBC は、以前のバージョンの Windows にのみ明示的にインストールしてください。  
  
 ドライバーセットアップ DLL には **、構成ドライバー**と**構成DSN**関数が含まれています。 **ConfigDriver**は、ドライバー固有の情報をレジストリに入力するなど、ドライバー固有のインストール タスクを実行します。 **ConfigDSN**は、レジストリ内のデータ ソースに関するドライバ固有の情報を保持します。 これらの関数の詳細については[、「DLL API リファレンスのセットアップ](../../../odbc/reference/syntax/setup-dll-api-reference.md)」を参照してください。  
  
 **ConfigDSN は**、レジストリ内のデータ ソース情報を維持するために、インストーラー DLL で次の関数を呼び出します。  
  
-   **を使用**します。 データ ソースを追加します。  
  
-   **イニから削除**します。 データ ソースを削除します。  
  
-   **をクリック**します。 データ ソース仕様サブキーの下にドライバー固有の値を記述します。  
  
-   を**クリック**します。 データ ソース仕様サブキーからドライバー固有の値を読み取ります。  
  
-   **トランスレータの取得** トランスレータ名とオプションをユーザーに求めるプロンプトを表示します。 この関数は、トランスレータ セットアップ DLL で**コントランスレータ**を呼び出します。  
  
 ドライバセットアップDLLはドライバ開発者によって書き込まれます。 ドライバ DLL の一部または別の DLL を指定できます。
