---
title: ドライバーのセットアップ DLL |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 088c9b60861266bf99649343aec2e763097bf155
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47786330"
---
# <a name="driver-setup-dll"></a>ドライバーのセットアップ DLL
> [!NOTE]  
>  ODBC は Windows XP および Windows Server 2003 以降、Windows オペレーティング システムに含まれます。 Windows の以前のバージョンで ODBC を明示的にのみインストールしてください。  
  
 ドライバーのセットアップ DLL が含まれています、 **ConfigDriver**と**ConfigDSN**関数。 **ConfigDriver**レジストリにドライバー固有の情報を入力するなどの個々 のドライバーのインストール タスクを実行します。 **ConfigDSN**レジストリ内のデータ ソースのドライバー固有の情報を保持します。 これらの関数の詳細については、次を参照してください。[セットアップ DLL API リファレンス](../../../odbc/reference/syntax/setup-dll-api-reference.md)します。  
  
 **ConfigDSN**インストーラー DLL レジストリ内のデータ ソース情報を維持するために、次の関数を呼び出します。  
  
-   **SQLWriteDSNToIni**します。 データ ソースを追加します。  
  
-   **SQLRemoveDSNFromIni**します。 データ ソースを削除します。  
  
-   **SQLWritePrivateProfileString**します。 データ ソースの仕様のサブキーの下のドライバー固有の値を記述します。  
  
-   **SQLGetPrivateProfileString**します。 データ ソースの仕様のサブキーからドライバー固有の値を読み取る。  
  
-   **SQLGetTranslator**します。 翻訳者名とオプションのユーザーを要求します。 この関数を呼び出す**ConfigTranslator**コンバーターで DLL のセットアップします。  
  
 ドライバーのセットアップ DLL は、ドライバーの開発者によって書き込まれます。 ドライバーの一部にすることができます、または別の DLL。
