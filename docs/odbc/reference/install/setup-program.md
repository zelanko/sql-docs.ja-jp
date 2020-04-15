---
title: セットアップ プログラム |マイクロソフトドキュメント
ms.custom: ''
ms.date: 08/31/2016
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
ms.assetid: 9cc5d75d-b293-41e5-927c-10f4af2e7af1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b89cae70db65bd2aa54b8e9789a5c2b35696923e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296152"
---
# <a name="setup-program"></a>セットアップ プログラム
> **注:** WINDOWS XP および Windows Server 2003 以降 **、ODBC は Windows の操作システムに含まれています**。 ODBC は、以前のバージョンの Windows にのみ明示的にインストールしてください。  
  
 ユーザーがセットアップ プログラムを実行して、セットアップ プロセスを開始します。 セットアップ プログラムは、アプリケーションまたはドライバーの開発者によって作成されます。 ODBC コンポーネントのインストールに加えて、他のソフトウェアをインストールすることもできます。 たとえば、アプリケーション開発者は、ODBC コンポーネントのインストールとアプリケーションのインストールの両方に同じセットアップ プログラムを使用できます。  
  
 開発者は、Microsoft® Windows® SDK セットアップ ユーティリティを使用して、セットアップ プログラムを最初から作成したり、他のベンダから提供されたセットアップ ソフトウェアを作成したりできます。 これにより、開発者はセットアップ プログラムのルック アンド フィールを完全に制御できます。 セットアップ プログラムを作成して、ODBC アプリケーションなどの追加のソフトウェアをインストールできます。 Windows SDK セットアップ ユーティリティの詳細については、Windows SDK のドキュメントを参照してください。  
  
 セットアップ プログラムによって実際に実行されるインストールの量は、インストーラ DLL で呼び出す関数によって異なります。 インストーラ DLL には、個々の ODBC コンポーネントをインストールする関数が含まれています。 セットアップ プログラムは、コンポーネントをインストールするディレクトリのパスを取得し、コンポーネントに関する情報をレジストリに追加するために、インストーラー DLL 内の**SQLInstallDriverManager** **、SQLInstallDriverEx**、または**SQLInstallTranslatorEx**を呼び出すだけです。 これらの関数は、実際にはファイルをコピーしません。セットアップ プログラムは、これらの関数の引数の情報を使用してこれを行います。  
  
 インストーラー DLL には、ODBC コンポーネントを削除する関数も含まれています。 セットアップ プログラムは、インストーラー DLL で**SQLRemoveDriverManager** **、SQLRemoveDriver**、または**SQLRemoveTranslator**を呼び出して、レジストリ内のコンポーネントの使用量カウントを減らします。 これらの関数は、実際にはコンポーネントのファイルを削除しません。セットアップ プログラムは、新しい使用カウントが 0 に下がった場合に、これを行います。
