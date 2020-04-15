---
title: 管理プログラム |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- administration program [ODBC]
- ODBC administrator [ODBC]
ms.assetid: a6c8248a-7a01-42e7-aaed-99dc94d50028
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d8a2a8363371d6f6c3644c2b7b49aa77644d496e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306643"
---
# <a name="administration-program"></a>管理プログラム
> [!NOTE]  
>  WINDOWS XP および Windows Server 2003 以降では、ODBC が Windows のオペレーション システムに含まれています。 ODBC は、以前のバージョンの Windows にのみ明示的にインストールしてください。  
  
 管理プログラムである ODBC アドミニストレーターは、Windows SDK/MDAC SDK に含まれています。 このプログラムは、SDK のユーザーが再配布できます。 さらに、開発者は独自の管理プログラムを作成できます。 一般に、開発者は、データ ソース構成を完全に制御する場合、または管理プログラムとして動作しているアプリケーションから直接データ ソースを構成する場合にのみ、独自の管理プログラムを作成します。 たとえば、スプレッドシート プログラムを使用すると、実行時にデータ ソースを追加して使用できます。  
  
 管理プログラムは、まずインストーラ DLL を読み込みます。 次に、インストーラ DLL の関数を呼び出して、次のタスクを実行します。  
  
-   **データ ソースを対話形式で追加、変更、または削除します。** 管理プログラムは **、SQL 管理データ**ソース **、SQLCreate データソース**、または**SQLConfigDataSource**を呼び出すことができます。  
  
     **SQLManageDataSources は**、ユーザーがデータ ソースを追加、変更、または削除したり、トレース オプションを指定できるダイアログ ボックスを表示します。この関数は、コントロール パネルから直接インストーラー DLL が呼び出されたときに呼び出されます。 **ユーザー**がデータ ソースを追加することしかできないダイアログ ボックスが表示されます。 **呼**び出しをドライバー セットアップ DLL に直接渡します。  
  
     すべての場合において、インストーラー DLL は、実際に追加、変更、またはデータ ソースを削除するドライバーセットアップ DLL で**ConfigDSN**を呼び出します。 ドライバーセットアップ DLL は、追加情報のユーザーを求める場合があります。  
  
-   **データ ソースをサイレントモードで追加、変更、または削除します。** 管理プログラムは、インストーラー DLL で**SQLConfigDataSource**を呼び出し、null ウィンドウ ハンドル、追加、変更、または削除するデータ ソースの名前、およびレジストリの値の一覧を渡します。 インストーラー DLL は、実際に追加、変更、またはデータ ソースを削除するドライバー セットアップ DLL で**ConfigDSN**を呼び出します。  
  
-   **既定のデータ ソースを追加、変更、または削除します。** 既定のデータ ソースは、その名前が [既定] である以外は、他のデータ ソースと同じです。 他のデータ ソースと同じ方法で追加、変更、または削除されます。
