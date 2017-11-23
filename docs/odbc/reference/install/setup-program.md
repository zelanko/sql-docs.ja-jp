---
title: "セットアップ プログラム |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/31/2016
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: installing ODBC components [ODBC], setup program
ms.assetid: 9cc5d75d-b293-41e5-927c-10f4af2e7af1
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 741ccfc8e9a096b60eca94b125890d48f65eb764
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="setup-program"></a>セットアップ プログラム
> **注:**以降では、Windows XP および Windows Server 2003、 **ODBC は、Windows オペレーティング システムに含まれる**です。 以前のバージョンの Windows で ODBC を明示的にのみインストールしてください。  
  
 ユーザーは、セットアップ プロセスを開始するセットアップ プログラムを実行します。 セットアップ プログラムは、アプリケーションまたはドライバーの開発者によって書き込まれます。 ODBC コンポーネントをインストールするだけでなく、その他のソフトウェアをインストールことできます。 たとえば、アプリケーション開発者は、ODBC コンポーネントをインストールして、アプリケーションをインストールする、同じセットアップ プログラムを使用可能性があります。  
  
 開発者ことができます、セットアップ プログラムを作成、最初から、Microsoft® Windows® SDK セットアップ ユーティリティまたはその他のベンダからセットアップ ソフトウェアを使用します。 これにより、開発者は、セットアップ プログラムのルック アンド フィールを完全に制御します。 ODBC アプリケーションなど、追加のソフトウェアをインストールするセットアップ プログラムを記述できます。 Windows SDK セットアップ ユーティリティの詳細については、Windows SDK のマニュアルを参照してください。  
  
 インストールの量を行うことも、セットアップ プログラムによっては、インストーラー DLL での呼び出し機能によって異なります。 DLL のインストーラーには、ODBC の個々 のコンポーネントをインストールする機能が含まれています。 セットアップ プログラムを呼び出すだけ**SQLInstallDriverManager**、 **SQLInstallDriverEx**、または**SQLInstallTranslatorEx**インストーラーのパスを取得するための DLL で、コンポーネントがインストールされると、コンポーネントの概要情報をレジストリに追加するディレクトリ。 これらの関数がファイルを実際にはコピーしないでください。セットアップ プログラムはこの情報を使用して、これらの関数の引数で行われます。  
  
 インストーラーの DLL には、ODBC コンポーネントを削除する関数も含まれています。 セットアップ プログラム呼び出し**SQLRemoveDriverManager**、 **SQLRemoveDriver**、または**SQLRemoveTranslator**内のインストーラーに、コンポーネントの使用状況をデクリメントするための DLL の数、レジストリと、コンポーネントの新しい使用状況カウントが 0 になった場合は、コンポーネントに関するすべての情報をレジストリから削除します。 これらの関数が、コンポーネントのファイルを実際には削除しないでください。新しい使用状況カウントが 0 になる場合はこのセットアップ プログラムによって行われます。
