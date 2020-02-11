---
title: ドライバーのアーキテクチャ |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fd9bbb74d77a0b56b6b1f1aa5d8f1a6b5e97f5aa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915470"
---
# <a name="driver-architecture"></a>ドライバーのアーキテクチャ
ドライバーアーキテクチャは、どのソフトウェアが SQL ステートメントを処理するかに応じて、2つのカテゴリに分類されます。  
  
-   **ファイルベースのドライバー**ドライバーは物理データに直接アクセスします。 この場合、ドライバーはドライバーとデータソースの両方として機能します。つまり、ODBC 呼び出しと SQL ステートメントを処理します。 たとえば、dbase ドライバーはファイルベースのドライバーです。これは、dBASE は、ドライバーが使用できるスタンドアロンデータベースエンジンを提供しないためです。 ファイルベースのドライバーの開発者は、独自のデータベースエンジンを作成する必要があることに注意してください。  
  
-   **DBMS ベースのドライバー**ドライバーは、独立したデータベースエンジンを使用して物理データにアクセスします。 この場合、ドライバーは ODBC 呼び出しのみを処理します。処理のために SQL ステートメントをデータベースエンジンに渡します。 たとえば、oracle ドライバーは、ドライバーが使用するスタンドアロンデータベースエンジンを備えているため、DBMS ベースのドライバーです。 データベースエンジンが存在する場所は問題でです。 ドライバーと同じコンピューター上に配置することも、ネットワーク上の別のコンピューターに配置することもできます。ゲートウェイ経由でアクセスすることもできます。  
  
 ドライバーのアーキテクチャは、通常、ドライバーライターにのみ興味深いものです。つまり、通常、ドライバーアーキテクチャではアプリケーションに違いはありません。 ただし、アーキテクチャは、アプリケーションで DBMS 固有の SQL を使用できるかどうかに影響を与える可能性があります。 たとえば、Microsoft Access では、スタンドアロンデータベースエンジンが提供されます。 Microsoft Access ドライバーが DBMS ベースの場合は、このエンジンを介してデータにアクセスします。アプリケーションは、処理のために Microsoft Access SQL ステートメントをエンジンに渡すことができます。  
  
 ただし、ドライバーがファイルベースである場合は、microsoft® Access .mdb ファイルに直接アクセスする独自のエンジンが含まれています。そのため、Microsoft Access 固有の SQL ステートメントをエンジンに渡そうとすると、構文エラーが発生する可能性があります。 これは、独自のエンジンが ODBC SQL のみを実装する可能性があるためです。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ファイル ベースのドライバー](../../odbc/reference/file-based-drivers.md)  
  
-   [DBMS ベースのドライバー](../../odbc/reference/dbms-based-drivers.md)  
  
-   [ネットワークの例](../../odbc/reference/network-example.md)  
  
-   [その他のドライバーのアーキテクチャ](../../odbc/reference/other-driver-architectures.md)
