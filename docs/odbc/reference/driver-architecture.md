---
title: ドライバアーキテクチャ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC], architecture
ms.assetid: c5003413-0cc1-4f41-b877-a64e2f5ab118
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ffe2023f028357468700b9bd995d22129ba06817
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294222"
---
# <a name="driver-architecture"></a>ドライバーのアーキテクチャ
ドライバー・アーキテクチャーは、SQL ステートメントを処理するソフトウェアに応じて、次の 2 つのカテゴリーに分類されます。  
  
-   **ファイルベースのドライバ**ドライバーは、物理データに直接アクセスします。 この場合、ドライバーはドライバーとデータ ソースの両方として機能します。つまり、ODBC 呼び出しと SQL ステートメントを処理します。 たとえば、dBASE ドライバーは、ドライバーが使用できるスタンドアロンデータベース エンジンを提供しないため、dBASE ドライバーは、ファイル ベースのドライバーです。 ファイル ベースのドライバーの開発者は、独自のデータベース エンジンを記述する必要があることに注意してください。  
  
-   **DBMS ベースのドライバ**ドライバーは、別のデータベース エンジンを介して物理データにアクセスします。 この場合、ドライバーは ODBC 呼び出しのみを処理します。SQL ステートメントをデータベース エンジンに渡して処理します。 たとえば、Oracle ドライバには、ドライバが使用するスタンドアロンのデータベース エンジンがあるため、Oracle ドライバは DBMS ベースのドライバです。 データベース エンジンが存在する場所は重要ではありません。 ドライバと同じマシンに配置することも、ネットワーク上の別のマシンに配置することもできます。ゲートウェイを介してアクセスすることもできます。  
  
 ドライバー アーキテクチャは、一般的に、ドライバーの作成者にのみ興味深いものです。つまり、ドライバーアーキテクチャは、一般的にアプリケーションに違いはありません。 ただし、このアーキテクチャーは、アプリケーションが DBMS 固有の SQL を使用できるかどうかに影響を与える可能性があります。 たとえば、Access にはスタンドアロン データベース エンジンが用意されています。 Access ドライバが DBMS ベースの場合、このエンジンを通じてデータにアクセスします。  
  
 ただし、ドライバがファイル ベースの場合、つまり、Microsoft® Access .mdb ファイルに直接アクセスする独自のエンジンが含まれています。 その理由は、独自のエンジンが ODBC SQL のみを実装する可能性が高いからである。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ファイル ベースのドライバー](../../odbc/reference/file-based-drivers.md)  
  
-   [DBMS ベースのドライバー](../../odbc/reference/dbms-based-drivers.md)  
  
-   [ネットワークの例](../../odbc/reference/network-example.md)  
  
-   [その他のドライバーのアーキテクチャ](../../odbc/reference/other-driver-architectures.md)
