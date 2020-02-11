---
title: マシンデータソース |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- machine data sources [ODBC]
- data sources [ODBC], machine
ms.assetid: 371bb5b5-1258-4657-acb5-d2b688b2ab4c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fe58e6e560ce4a538290b9f87e99bb4f22e12aab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68062648"
---
# <a name="machine-data-sources"></a>マシン データ ソース
*コンピューターのデータソース*は、ユーザー定義の名前を使用してシステムに格納されます。 データソース名に関連付けられているのは、ドライバーマネージャーとドライバーがデータソースに接続するために必要なすべての情報です。 Xbase データソースの場合、Xbase ドライバーの名前、Xbase ファイルが格納されているディレクトリの完全パス、およびそれらのファイルの使用方法をドライバーに指示するオプション (シングルユーザーモードや読み取り専用など) が考えられます。 Oracle データソースの場合は、oracle ドライバーの名前、Oracle DBMS が配置されているサーバー、使用する SQL\*net ドライバーを識別する Sql * net 接続文字列、およびサーバー上のデータベースのシステム ID を指定できます。
