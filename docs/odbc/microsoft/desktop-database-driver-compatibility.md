---
description: デスクトップ データベース ドライバーの互換性
title: デスクトップデータベースドライバーの互換性 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], Unicode
- Unicode [ODBC], desktop database drivers
- ODBC desktop database drivers [ODBC], Unicode
- backward compatibility [ODBC], Unicode
- desktop database drivers [ODBC], Unicode
- Jet-based ODBC drivers [ODBC], Unicode
ms.assetid: dd695638-1a0b-4e27-8a6a-9510ebb5a5ee
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6b15ec35a01b61eef401f217733917a80bbe32b4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340778"
---
# <a name="desktop-database-driver-compatibility"></a>デスクトップ データベース ドライバーの互換性
Unicode は、すべての文字を2バイトの固定幅として扱う、ソフトウェア文字エンコーディングの方法です。 このメソッドは、Windows ANSI 文字エンコーディングの代わりに使用されます。これは、1バイトの文字を表すため、256文字に制限されます。 Unicode は65000文字を超えることができるため、ANSI エンコーディングでは文字が表現されない多くの言語に対応します。  
  
 ODBC 3.5 (またはそれ以降) ドライバーマネージャーが Unicode 対応になっています。 これは、関数呼び出しと文字列データ型の2つの主な領域に影響します。 ドライバーマネージャーは、関数の文字列引数と文字列データを、アプリケーションとドライバーの必要に応じてマップします。どちらも、Unicode 対応または ANSI 対応のどちらでもかまいません。  
  
 ODBC 3.5 (またはそれ以降) のドライバーマネージャーでは、unicode アプリケーションと ANSI アプリケーションの両方を使用した Unicode ドライバーの使用がサポートされています。 Ansi アプリケーションでの ANSI ドライバーの使用もサポートしています。 ドライバーマネージャーでは、ANSI ドライバーを使用する Unicode アプリケーションに対して、Unicode から ANSI へのマッピングが制限されています。 これにより、Jet 3.5 データベースにアクセスし、すべての既存の ISAM ファイルの種類をサポートできます。  
  
 ANSI アプリケーションで ODBC デスクトップデータベースドライバー4.0 を使用していて、Microsoft Access 4.0 以降にアクセスする場合、Jet 4.0 ではワイドバージョンがサポートされていますが、ドライバーは SQL_CHAR、SQL_VARCHAR、または SQL_LONGVARCHAR としてデータ型を公開します。 以前のバージョンの Jet では、SQL_WCHAR、SQL_WVARCHAR、および SQL_WLONGVARCHAR はサポートされていません。 この制限は、Jet 4.0 データベースエンジンで古い形式が使用されている場合にも適用されます。  
  
 ODBC に関する Unicode の問題の詳細については、「プログラミングにおける [unicode](../../odbc/reference/develop-app/unicode.md) の考慮事項」を参照してください。
