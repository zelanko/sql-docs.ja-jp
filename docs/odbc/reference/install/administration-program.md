---
title: "管理プログラム |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- administration program [ODBC]
- ODBC administrator [ODBC]
ms.assetid: a6c8248a-7a01-42e7-aaed-99dc94d50028
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 53024c6d7ba7933ae6bcc425455b262b176fed80
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="administration-program"></a>管理プログラム
> [!NOTE]  
>  Windows XP および Windows Server 2003 以降、Windows オペレーティング システムに ODBC が含まれます。 以前のバージョンの Windows で ODBC を明示的にのみインストールしてください。  
  
 管理プログラム、ODBC アドミニストレーターは、Windows SDK/MDAC SDK に含まれています。 このプログラムし、SDK のユーザーによって再配布できます。 さらに、開発者は、独自の管理プログラムを作成できます。 一般に、開発者は、データ ソースの構成を完全に制御を維持する場合にのみ、または管理プログラムとして機能しているアプリケーションから直接データ ソースを構成する場合は、独自の管理プログラムを記述します。 たとえば、スプレッドシート プログラムは、ユーザーを追加し、実行時にデータ ソースを使用を許可する可能性があります。  
  
 まず、管理プログラムは、インストーラー DLL を読み込みます。 インストーラーは次のタスクを実行するための DLL で関数を呼び出します。  
  
-   **追加、変更、または対話形式でデータ ソースを削除します。** 管理プログラムで呼び出すことができます**SQLManageDataSources**、 **SQLCreateDataSource**、または**SQLConfigDataSource**です。  
  
     **SQLManageDataSources**使用するユーザーを追加、変更、またはデータ ソースを削除するオプションを指定できますトレース; インストーラー DLL は、コントロール パネルから直接呼び出されたときに、この関数が呼び出されます ダイアログ ボックスが表示されます。 **SQLCreateDataSource**いるユーザーはのみのデータ ソースを追加 ダイアログ ボックスが表示されます。 **SQLConfigDataSource**ドライバーのセットアップ DLL を直接呼び出しを渡します。  
  
     インストーラーの DLL を呼び出す場合は、 **ConfigDSN**ドライバー セットアップ DLL に実際に追加するには、変更、またはデータ ソースを削除します。 ドライバーのセットアップ DLL を追加情報を求める場合があります。  
  
-   **追加、変更、またはサイレント モードでのデータ ソースを削除します。** 管理プログラム呼び出し**SQLConfigDataSource**インストーラー DLL とパスで、null のウィンドウを処理、追加、変更、または削除するデータ ソースの名前と、レジストリの値の一覧です。 インストーラー DLL 呼び出し**ConfigDSN**ドライバー セットアップ DLL に実際に追加するには、変更、またはデータ ソースを削除します。  
  
-   **追加、変更、または既定のデータ ソースを削除します。** 既定のデータ ソースは、その名前が既定する点を除いて、他のデータ ソースとして同じです。 追加、変更されると、またはその他のデータ ソースと同じ方法で削除します。
