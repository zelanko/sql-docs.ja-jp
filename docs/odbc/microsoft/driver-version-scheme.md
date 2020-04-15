---
title: ドライババージョンスキーム |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], versions
ms.assetid: e4a8d9d7-8aba-48ab-8be6-1a6129adfb8f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 864a8bd892315b060fc6fcf42dbe69dfea61ae59
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303453"
---
# <a name="driver-version-scheme"></a>ドライバー バージョン スキーム
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 次の表は、Oracle 用のマイクロソフト ODBC ドライバーのすべてのリリースバージョンを示しています。  
  
|ドライバーのバージョン|ビルド番号|可用性の履歴|  
|--------------------|------------------|--------------------------|  
|1.0|2.00.6235|Visual C++ 4.2 および Visual Basic 5.0、エンタープライズ エディション|  
|2.0|2.73.7269|ビジュアル スタジオ 97 および MDAC 1.5a|  
|2.0 が更新されました|2.73.7283.01|IIS 4.0|  
|2.0 が更新されました|2.73.7283.03|MDAC 1.5bおよび1.5c|  
|2.0 が更新されました|2.73.7356|ODBC 3.5 SDK|  
|2.5|2.573.2927|ビジュアル スタジオ 6.0 および MDAC 2.0|  
|2.5 更新|2.573.3513|SQL サーバー 7.0<br /><br /> SQL サーバー 6.5 SP5|  
  
 ビルド 2.00.6235 (バージョン 1) は、Oracle 用のマイクロソフト ODBC ドライバーの最初のリリースでした。 最初のバージョンのリリース後、新しい命名規則が採用されました。  
  
 たとえば、2.73.7283.03 は、次の個別のコンポーネントに分割できます。  
  
-   2 = バージョン番号。  
  
-   73 = ドライバが設計された Oracle サーバのバージョン。  
  
-   7283.03 = ドライバのビルド番号。  
  
> [!NOTE]  
>  リリース 2.573.2973 では、名前付け規則によって、2.573 が 2.73 より前のリリースであるという混乱が生じましたが、ビルド番号の各セクションは個別に考慮する必要があります。 573 という数字は 73 より大きいので、新しいバージョンです。 また、"2.5" は、ドライバーのバージョン番号を示します。
