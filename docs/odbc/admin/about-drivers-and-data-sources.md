---
title: ドライバーとデータ ソースについて |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC data source administrator [ODBC], concepts
ms.assetid: 2bb83ef1-4bbe-4be3-8c32-c4d1140aae1d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 69516a613cbd9071686067350ced2ce5ca166a27
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47776050"
---
# <a name="about-drivers-and-data-sources"></a>ドライバーとデータ ソースについて
*ドライバー*は ODBC の要求を処理し、アプリケーションにデータを返すコンポーネントです。 必要に応じて、ドライバーは、データ ソースで認識できる形式にアプリケーションの要求を変更します。 ドライバーのセットアップ プログラムを使用して、追加またはドライバーをコンピューターから削除する必要があります。  
  
 *データ ソース*データベースと、ドライバーによってアクセスされたファイル、およびデータ ソース名 (DSN) によって識別されます。 ODBC データ ソース アドミニストレーターを使用して、追加、構成、およびシステムからデータ ソースを削除します。 次の表は、使用できるデータ ソースの種類を説明します。  
  
|データ ソース|説明|  
|-----------------|-----------------|  
|ユーザー|ユーザー Dsn はコンピューターにローカルであり、現在のユーザーによってのみ使用できます。 これらは、HKEY_CURRENT_USER レジストリ サブツリーに登録されます。|  
|システム|システム Dsn は、専用のユーザーではなく、コンピューターに対してローカルです。 システムまたは特権を持つ任意のユーザーは、データ ソースがシステム DSN を使用して設定を使用できます。 システム Dsn は、レジストリの HKEY_LOCAL_MACHINE サブツリーに登録されます。|  
|ファイル|ファイル Dsn は、同じドライバーがインストールされているすべてのユーザー間で共有することができますし、そのため、データベースへのアクセスを持つファイル ベースのソースです。 これらのデータ ソースは、ユーザーには専用ない必要がありますも、コンピューターにローカルでいます。 ファイル データ ソース名は専用のレジストリ エントリを識別しません。代わりに、拡張子が .dsn ファイル名によって識別されます。|  
  
 ユーザーおよびシステムのデータ ソースと総称されます*マシン*データ ソースのコンピューターに対してローカルにいるためです。  
  
 タブが、これらのデータ ソースの各、 **ODBC データ ソース アドミニストレーター**  ダイアログ ボックス。 使用できるデータ ソースの詳細については、「 [データ ソース](../../odbc/reference/data-sources.md)」を参照してください。
