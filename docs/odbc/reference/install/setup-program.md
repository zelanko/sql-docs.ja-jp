---
title: セットアップ プログラム |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/31/2016
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
ms.assetid: 9cc5d75d-b293-41e5-927c-10f4af2e7af1
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22424b9462f5ed2174f23d5db9ff95ad7191f281
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="setup-program"></a>セットアップ プログラム
> **注:** 以降では、Windows XP および Windows Server 2003、 **ODBC は、Windows オペレーティング システムに含まれる**です。 以前のバージョンの Windows で ODBC を明示的にのみインストールしてください。  
  
 ユーザーは、セットアップ プロセスを開始するセットアップ プログラムを実行します。 セットアップ プログラムは、アプリケーションまたはドライバーの開発者によって書き込まれます。 ODBC コンポーネントをインストールするだけでなく、その他のソフトウェアをインストールことできます。 たとえば、アプリケーション開発者は、ODBC コンポーネントをインストールして、アプリケーションをインストールする、同じセットアップ プログラムを使用可能性があります。  
  
 開発者ことができます、セットアップ プログラムを作成、最初から、Microsoft® Windows® SDK セットアップ ユーティリティまたはその他のベンダからセットアップ ソフトウェアを使用します。 これにより、開発者は、セットアップ プログラムのルック アンド フィールを完全に制御します。 ODBC アプリケーションなど、追加のソフトウェアをインストールするセットアップ プログラムを記述できます。 Windows SDK セットアップ ユーティリティの詳細については、Windows SDK のマニュアルを参照してください。  
  
 インストールの量を行うことも、セットアップ プログラムによっては、インストーラー DLL での呼び出し機能によって異なります。 DLL のインストーラーには、ODBC の個々 のコンポーネントをインストールする機能が含まれています。 セットアップ プログラムを呼び出すだけ**SQLInstallDriverManager**、 **SQLInstallDriverEx**、または**SQLInstallTranslatorEx**インストーラーのパスを取得するための DLL で、コンポーネントがインストールされると、コンポーネントの概要情報をレジストリに追加するディレクトリ。 これらの関数がファイルを実際にはコピーしないでください。セットアップ プログラムはこの情報を使用して、これらの関数の引数で行われます。  
  
 インストーラーの DLL には、ODBC コンポーネントを削除する関数も含まれています。 セットアップ プログラム呼び出し**SQLRemoveDriverManager**、 **SQLRemoveDriver**、または**SQLRemoveTranslator**内のインストーラーに、コンポーネントの使用状況をデクリメントするための DLL の数、レジストリと、コンポーネントの新しい使用状況カウントが 0 になった場合は、コンポーネントに関するすべての情報をレジストリから削除します。 これらの関数が、コンポーネントのファイルを実際には削除しないでください。新しい使用状況カウントが 0 になる場合はこのセットアップ プログラムによって行われます。
