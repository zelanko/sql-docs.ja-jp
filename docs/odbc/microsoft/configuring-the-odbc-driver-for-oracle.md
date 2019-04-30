---
title: Oracle 用 ODBC ドライバーの構成 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae444cfb293e12bd94281957335da1d4f4a97885
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63301747"
---
# <a name="configuring-the-odbc-driver-for-oracle"></a>ODBC Driver for Oracle の構成
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 データ環境を把握し、経由したデータ ソース接続のパラメーターを正しく設定して、ODBC Driver for Oracle のパフォーマンスを制御できます、 [ODBC データ ソース アドミニストレーター](../../odbc/admin/odbc-data-source-administrator.md)  ダイアログ ボックスまたはを介して接続します。文字列パラメーター。 ダイアログ ボックスには、ダイアログ ボックスを使用してデータ ソースに接続するための次のコントロールが用意されていますかを使用して接続文字列。  
  
-   **[ユーザー DSN] タブ**コンピューターに対してローカルなデータ ソース名が表示されます。  
  
-   **[システム DSN] タブ**を追加またはシステム データ ソースを削除することができます。 システム データ ソースは、ローカル コンピューター上のすべてのユーザーがアクセスできます。  
  
-   **[ファイル DSN] タブ**を追加またはローカル コンピューターからファイルのデータ ソースを削除することができます。 ファイル データ ソースは、同じドライバーがインストールされているすべてのユーザーで共有できます。  
  
-   **[ドライバー] タブ**インストールされている ODBC ドライバーの一覧を表示します。  
  
-   **[トレース] タブ**ODBC ドライバー マネージャーが ODBC 関数呼び出しをトレースする方法を指定することができます。 個別にインストールされている各 ODBC アプリケーションのトレースを構成することができます。  
  
-   **接続プール タブ**インストールされている各ドライバーの接続オプションを選択することができます。  
  
-   **タブに関する**インストールされた ODBC コンポーネント ファイルを一覧表示されます。  
  
 使用することができます、データ ソースを追加した後、 **ODBC データ ソース アドミニストレーター**ダイアログ ボックスを使用するデータ ソースへのアクセスを構成します。 データ ソースを選択し、編集、または情報を確認するには、タブのいずれかをクリックします。
