---
title: デスクトップ データベース ドライバー互換性 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
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
- compatibility [ODBC], Unicode
- Unicode [ODBC], desktop database drivers
- ODBC desktop database drivers [ODBC], Unicode
- backward compatibility [ODBC], Unicode
- desktop database drivers [ODBC], Unicode
- Jet-based ODBC drivers [ODBC], Unicode
ms.assetid: dd695638-1a0b-4e27-8a6a-9510ebb5a5ee
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 557a7254e9cea7476ee3de706da86519f9ef1fec
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="desktop-database-driver-compatibility"></a>デスクトップ データベース ドライバーの互換性
Unicode は、ソフトウェア文字エン コードのメソッドのすべての文字を 2 バイトの固定幅を持つものとして扱われます。 このメソッドは、Windows の ANSI 文字エン コード、1 バイトの文字を表すためでは、256 文字に制限の代わりとして使用されます。 文字から成るは表されない多くの言語に対応 Unicode が 65,000 以上の文字を表すことのできるために、ANSI エンコーディングします。  
  
 ODBC 3.5 (またはそれ以降) ドライバー マネージャーは、Unicode に対応します。 2 つの主要な領域に影響します。 関数呼び出しと、文字列データ型。 ドライバー マネージャー マップ関数の文字列引数と文字列データは、アプリケーションおよびドライバーによって必要に応じては Unicode に対応するか、ANSI が有効なをどちらもできます。  
  
 ODBC 3.5 (またはそれ以降) のドライバー マネージャーは、Unicode アプリケーションと ANSI アプリケーションの両方で Unicode ドライバーの使用をサポートします。 ANSI アプリケーションと ANSI ドライバーの使用もサポートします。 ドライバー マネージャーは、Unicode アプリケーションの場合、ANSI ドライバーの使用の制限の Unicode から ANSI へマッピングを提供します。 これは、Jet 3.5 データベースおよびすべての既存 ISAM ファイルの種類のサポートへのアクセスを許可します。  
  
 ANSI アプリケーションが ODBC デスクトップ データベース ドライバー 4.0 を使用し、Microsoft Access 4.0 にアクセスするか、後で、ドライバーとして公開するデータ型 SQL_CHAR、sql_varchar、SQL_LONGVARCHAR Jet 4.0 には、ワイド バージョンがサポートされています。 です。 以前のバージョンの Jet では、SQL_WCHAR、SQL_WVARCHAR、SQL_WLONGVARCHAR は使用できません。 この制限は、Jet 4.0 データベース エンジンと古い形式が使用されている場合にも適用されます。  
  
 ODBC と Unicode の問題に関する詳細については、次を参照してください。 [Unicode](../../odbc/reference/develop-app/unicode.md)プログラミングの考慮事項です。
