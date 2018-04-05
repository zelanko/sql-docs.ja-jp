---
title: ドライバーおよびデータ ソースに関する |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ODBC data source administrator [ODBC], concepts
ms.assetid: 2bb83ef1-4bbe-4be3-8c32-c4d1140aae1d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6422e855b126245fd7118ce2518538aa0305484a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="about-drivers-and-data-sources"></a>ドライバーとデータ ソースについて
*ドライバー* ODBC 要求を処理し、アプリケーションにデータを返すコンポーネントはインストールされています。 必要に応じて、ドライバーは、データ ソースで認識できる形式にアプリケーションの要求を変更します。 ドライバーのセットアップ プログラムを使用して、追加またはドライバーをコンピューターから削除する必要があります。  
  
 *データ ソース*データベースやドライバーによってアクセスされたファイルは、データ ソース名 (DSN) によって識別されます。 ODBC データ ソース アドミニストレーターを使用して、追加、構成、およびシステムからデータ ソースを削除します。 使用できるデータ ソースの種類は次の表で説明します。  
  
|データ ソース|Description|  
|-----------------|-----------------|  
|ユーザー|ユーザー Dsn は、コンピューターにローカルであり、現在のユーザーによってのみ使用できます。 これらは、HKEY_CURRENT_USER レジストリ サブツリーに登録されます。|  
|システム|システム Dsn は、ユーザー専用ではなく、コンピューターに対してローカルです。 システムまたは特権を持つユーザーは、システム DSN を設定、データ ソースを使用できます。 システム Dsn は、レジストリの HKEY_LOCAL_MACHINE サブツリーに登録されます。|  
|ファイル|ファイル Dsn は、同じドライバーがインストールされているすべてのユーザー間で共有することができますし、そのため、データベースへのアクセスを持つファイル ベースのソースです。 これらのデータ ソースは必要ありません専用にするユーザーも、コンピューターに対してローカルでいます。 ファイル データ ソース名は専用のレジストリ エントリでは識別されません。代わりに、.dsn 拡張子の付いたファイル名によって識別されます。|  
  
 ユーザーおよびシステム データ ソースは、として総称*マシン*データ ソースをローカル コンピューターにあるためです。  
  
 これらのデータ ソースは、タブ、 **ODBC データ ソース アドミニストレーター**  ダイアログ ボックス。 使用できるデータ ソースの詳細については、「 [データ ソース](../../odbc/reference/data-sources.md)」を参照してください。
