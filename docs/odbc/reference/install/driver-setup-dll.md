---
title: "ドライバーのセットアップ DLL |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing ODBC components [ODBC], driver setup DLL
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: 49bab021-81fa-402e-b7a4-a5214f1fadc4
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d75a8985feff2ddfe26d3e19e8bafd91f228d30e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="driver-setup-dll"></a>ドライバーのセットアップ DLL
> [!NOTE]  
>  Windows XP および Windows Server 2003 以降、Windows オペレーティング システムに ODBC が含まれます。 以前のバージョンの Windows で ODBC を明示的にのみインストールしてください。  
  
 DLL を含むドライバーのセットアップ、 **ConfigDriver**と**ConfigDSN**関数。 **ConfigDriver**レジストリにドライバー固有の情報を入力するなどの個々 のドライバーのインストール タスクを実行します。 **ConfigDSN**レジストリ内のデータ ソースのドライバー固有の情報を保持します。 これらの関数の詳細については、次を参照してください。[セットアップ DLL の API リファレンス](../../../odbc/reference/syntax/setup-dll-api-reference.md)です。  
  
 **ConfigDSN**インストーラー レジストリ内のデータ ソース情報を維持するための DLL で、次の関数を呼び出します。  
  
-   **SQLWriteDSNToIni**です。 データ ソースを追加します。  
  
-   **SQLRemoveDSNFromIni**です。 データ ソースを削除します。  
  
-   **SQLWritePrivateProfileString**です。 データ ソースの仕様のサブキーの下のドライバー固有の値を記述します。  
  
-   **SQLGetPrivateProfileString**です。 データ ソースの仕様サブキーからドライバー固有の値を読み取る。  
  
-   **SQLGetTranslator**です。 翻訳者名とオプションのユーザーを要求します。 この関数が呼び出す**ConfigTranslator**コンバーターで DLL をセットアップします。  
  
 ドライバーのセットアップ DLL は、ドライバーの開発者によって書き込まれます。 ドライバーの一部にすることができます、または別の DLL。

