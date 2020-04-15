---
title: Oracle 用の ODBC ドライバの設定 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- configuring ODBC driver for Oracle [ODBC]
- ODBC driver for Oracle [ODBC], configuring
ms.assetid: 0a5f827c-0b80-4627-85cb-f10292b9fb33
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1bbdbe36ed9e6f254e2b738479698bd9eece09f8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281372"
---
# <a name="configuring-the-odbc-driver-for-oracle"></a>ODBC Driver for Oracle の構成
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 データ環境を把握し、ODBC[データ ソース アドミニストレータ](../../odbc/admin/odbc-data-source-administrator.md)ダイアログ ボックスまたは接続文字列パラメーターを使用して、データ ソース接続のパラメーターを正しく設定することで、Oracle 用 ODBC ドライバーのパフォーマンスを制御できます。 ダイアログ ボックスには、ダイアログ ボックスを使用してデータ ソースに接続したり、接続文字列を使用したりするための次のコントロールがあります。  
  
-   **[ユーザー DSN] タブ**コンピュータに対してローカルなデータ ソース名の一覧が表示されます。  
  
-   **[システム DSN] タブ**システム データ ソースを追加または削除できます。 システム データ ソースには、ローカル コンピューター上のすべてのユーザーがアクセスできます。  
  
-   **[ファイル DSN] タブ**ローカル コンピューターにファイル データ ソースを追加またはローカル コンピューターから削除できます。 ファイル データ ソースは、同じドライバーがインストールされているすべてのユーザーが共有できます。  
  
-   **[ドライバ]タブ**インストールされている ODBC ドライバの一覧が表示されます。  
  
-   **[トレース] タブ**ODBC ドライバー マネージャーが ODBC 関数の呼び出しをトレースする方法を指定できます。 インストールされている ODBC アプリケーションごとに、トレースを個別に構成できます。  
  
-   **[接続プール] タブ**インストールされている各ドライバの接続オプションを選択できます。  
  
-   **タブについて**インストールされている ODBC コンポーネント ファイルの一覧が表示されます。  
  
 データ ソースを追加した後 **、[ODBC データ ソース アドミニストレータ**] ダイアログ ボックスを使用して、データ ソースへのアクセスを構成できます。 データ ソースを選択し、いずれかのタブをクリックして、情報を編集または確認します。
