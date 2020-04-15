---
title: デスクトップ データベース ドライバの互換性 |マイクロソフトドキュメント
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
ms.openlocfilehash: 89eea7ab112eaefdc73c7cbc72ee3555797c7efd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303523"
---
# <a name="desktop-database-driver-compatibility"></a>デスクトップ データベース ドライバーの互換性
Unicode は、すべての文字を固定長 2 バイトとして扱うソフトウェア文字エンコード方式です。 このメソッドは、Windows ANSI 文字エンコードの代替として使用され、1 バイトの文字を表すため、256 文字に制限されます。 Unicode は 65,000 文字を超える文字を表すことができるため、ANSI エンコードでは文字が表されない多くの言語に対応しています。  
  
 ODBC 3.5 以降のドライバ マネージャは、Unicode 対応です。 これは、関数呼び出しと文字列データ型という 2 つの主要な領域に影響します。 ドライバー マネージャーは、アプリケーションとドライバーの要求に応じて、関数の文字列引数と文字列データをマップします。  
  
 ODBC 3.5 以降のドライバー マネージャーは、Unicode アプリケーションと ANSI アプリケーションの両方で、Unicode ドライバーの使用をサポートします。 また、ANSI アプリケーションで ANSI ドライバーを使用することもできます。 ドライバー マネージャーは、ANSI ドライバーを使用して作業する Unicode アプリケーションの限定された Unicode から ANSI へのマッピングを提供します。 これにより、Jet 3.5 データベースにアクセスでき、既存のすべての ISAM ファイルの種類をサポートできます。  
  
 ANSI アプリケーションが ODBC デスクトップ データベース ドライバ 4.0 を使用して Access 4.0 以降にアクセスすると、Jet 4.0 がワイド バージョンをサポートしているにもかかわらず、ドライバはデータ型をSQL_CHAR、SQL_VARCHAR、またはSQL_LONGVARCHARとして公開します。 古いバージョンの Jet では、SQL_WCHAR、SQL_WVARCHAR、およびSQL_WLONGVARCHARはサポートされていません。 この制限は、Jet 4.0 データベース エンジンで古い形式が使用される場合にも適用されます。  
  
 ODBC でのユニコードの問題の詳細については、プログラミングの考慮事項の[ユニコード](../../odbc/reference/develop-app/unicode.md)を参照してください。
