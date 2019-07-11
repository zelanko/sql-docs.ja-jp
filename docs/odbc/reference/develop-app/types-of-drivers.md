---
title: ドライバーの種類 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
ms.assetid: 864c53c1-b68a-48b6-b6bc-5ecb520bb9dc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 08c1c9b4338502f20e5f99885d371d713971aa38
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792702"
---
# <a name="types-of-drivers"></a>ドライバーの種類
ODBC ドライバーは、次のように分類できます。  
  
-   **32 ビット ODBC 2.**  
     **_x_ドライバー** 32 ビットのドライバーです。  
  
    -   ODBC のみをエクスポートします*2.x*関数。  
  
    -   ODBC の欠落を表す*2.x*動作の変更点の動作。  
  
-   **ISO と開いているグループ準拠のドライバー** 32 ビット ドライバーです。  
  
    -   グループを開くまたは ISO CLI のドキュメントで説明されているすべての関数をエクスポートします。 ODBC では非推奨の機能の一部を含めます。  
  
    -   動作の変更点の ODBC 3.0 現象が発生します。  
  
    -   ODBC 3.0 のドライバー マネージャーを必ずしも通過しません。  
  
-   **ODBC 3.0 ドライバー** 32 ビットのドライバーです。  
  
    -   非推奨の関数-ODBC 3.0 では関数だけをエクスポートします。  
  
    -   ODBC が発生することのできる*2.x* SQL_ATTR_APP_ODBC_VERSION 環境属性に基づいて動作または動作の変更に関する ODBC 3.0 動作します。  
  
-   **ODBC 3.5 (またはそれ以降) の ANSI ドライバー** 32 ビットのドライバーです。  
  
    -   非推奨の関数-ODBC 3.5 では関数だけをエクスポートします。  
  
    -   ODBC が発生することのできる*2.x* SQL_ATTR_APP_ODBC_VERSION 環境属性に基づいて動作または ODBC 3.0 の動作または動作の変更に関して、ODBC 3.5 動作します。  
  
-   **ODBC 3.5 (またはそれ以降) の Unicode ドライバー** 32 ビットのドライバーです。  
  
    -   ODBC 3.5 ANSI ドライバーのすべての機能をサポートしています。  
  
    -   ODBC 文字列 Api のすべての Unicode バージョンをエクスポートします。  
  
    -   データ ソース上の Unicode データの処理し、格納できます。  
  
> [!NOTE]  
>  16 ビット ODBC ドライバーは、ODBC で直接は動作しません*3.x*ドライバー マネージャー。 ただし、その後最大サンク 2.0 ODBC ドライバー マネージャーを使用する 16 ビットのドライバーのことが、 *3.x*ドライバー マネージャー。
