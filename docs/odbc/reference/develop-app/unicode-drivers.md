---
title: ユニコードドライバー |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], drivers
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: 3b4742d5-74fb-4aff-aa21-d83a0064d73d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: aabdd899d78c1141716725d57e343dc002dc96ad
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284354"
---
# <a name="unicode-drivers"></a>Unicode ドライバー
ドライバーが Unicode ドライバーまたは ANSI ドライバーのどちらであるかは、データ ソースの性質に完全に依存します。 データ ソースが Unicode データをサポートしている場合、ドライバーは Unicode ドライバーである必要があります。 データ ソースが ANSI データのみをサポートしている場合、ドライバーは ANSI ドライバーのままにする必要があります。  
  
 ドライバー マネージャーによって Unicode ドライバーとして認識される**SQLConnectW**をエクスポートする必要があります。  
  
 Unicode ドライバーは *、(W*のサフィックスを持つ) Unicode 関数を受け入れ、Unicode データを格納する必要があります。 ANSI 関数を受け入れることもできますが、必須ではありません。 (ドライバー マネージャーは *、A*サフィックスを持つ ANSI 関数呼び出しを渡しませんが、サフィックスなしの ANSI 関数呼び出しに変換し、ドライバーに渡します)。  
  
 Unicode ドライバーは、アプリケーションのバインドに応じて、Unicode または ANSI のいずれかで結果セットを返すことができる必要があります。 アプリケーションがSQL_C_CHARにバインドする場合、Unicode ドライバーは、SQL_WCHARデータをSQL_CHARに変換する必要があります。 ドライバー マネージャーは、SQL_C_CHARに、ANSI ドライバーのSQL_C_WCHARをマップしますが、Unicode ドライバーのマッピングは行いません。  
  
> [!NOTE]  
>  ドライバーの種類を決定する場合、ドライバー マネージャーは**SQLSetConnectAttr**を呼び出し、接続時にSQL_ATTR_ANSI_APP属性を設定します。 アプリケーションが ANSI API を使用している場合、SQL_ATTR_ANSI_APPは SQL_AA_TRUE に設定され、Unicode を使用している場合は値がSQL_AA_FALSE に設定されます。 この属性は、ドライバーがアプリケーションの種類に基づいて異なる動作を表示できるように使用されます。 この属性は、アプリケーションで直接設定することはできず、 **SQLGetConnectAttr**ではサポートされていません。 ANSI アプリケーションと Unicode アプリケーションの両方で同じ動作をするドライバーは、この属性のSQL_ERROR返す必要があります。 ドライバーがSQL_SUCCESS返す場合、ドライバー マネージャーは、接続プールを使用するときに、ANSI と Unicode 接続を分離します。
