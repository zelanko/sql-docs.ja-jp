---
title: "ドライバー バージョン スキーム |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], versions
ms.assetid: e4a8d9d7-8aba-48ab-8be6-1a6129adfb8f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e3a8132d535b764818fb9dcab72b3cba8bb48154
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="driver-version-scheme"></a>ドライバー バージョン スキーム
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 次の表では、Microsoft ODBC Driver for Oracle のすべてのリリース バージョンが一覧表示します。  
  
|ドライバーのバージョン|ビルド番号|可用性の履歴|  
|--------------------|------------------|--------------------------|  
|1.0|2.00.6235|Visual C 4.2 および Visual Basic 5.0 では、Enterprise Edition|  
|2.0|2.73.7269|Visual Studio 97 および MDAC 1.5 a|  
|2.0 の更新|2.73.7283.01|IIS 4.0|  
|2.0 の更新|2.73.7283.03|MDAC 1.5b および 1.5 c|  
|2.0 の更新|2.73.7356|ODBC 3.5 SDK|  
|2.5|2.573.2927|Visual Studio 6.0 および MDAC 2.0|  
|2.5 の更新|2.573.3513|SQL Server 7.0<br /><br /> SQL Server 6.5 SP5|  
  
 ビルド 2.00.6235 (バージョン 1) は、Microsoft ODBC Driver for Oracle の最初のリリースでした。 最初のバージョンのリリースでは後、新しい名前付け規則を採用されました。  
  
 たとえば、2.73.7283.03 は、次の異なるコンポーネントに分類できます。  
  
-   2 = バージョン番号。  
  
-   73 ドライバーの設計対象となる Oracle サーバーのバージョンを = です。  
  
-   7283.03 ドライバーのビルド番号を = です。  
  
> [!NOTE]  
>  リリース 2.573.2973 は、名前付け規則の原因がいくつかの混乱 2.573 2.73 より以前のリリースがあるビルド番号の各セクションを個別に考慮する必要があります。 573 は 73 より大きいのでより新しいバージョンであります。 また、「2.5」は、ドライバーのバージョン番号を示します。
