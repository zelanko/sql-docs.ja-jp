---
title: 機能のサポートと可変性の確認 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: ff45f220-9b8b-4c44-82f8-a8e9913fffea
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 47f16160c05d1c410e3889f0bb857befe88df5b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299172"
---
# <a name="checking-feature-support-and-variability"></a>機能のサポートと可変性の確認
機能のサポートと可変性を確認するために、アプリケーションは通常 **、SQLGetInfo** **、SQLGetFunctions**、および**SQLGetTypeInfo**を呼び出します。 開始点として、ドライバーの API と SQL 文法の準拠レベルがあります。 これらは、幅広いレベルの機能サポートを表します。 アプリケーションは、その他のオプションを使用して**SQLGetInfo**を呼び出して、必要な機能のサポートまたは可変性を決定し、返された準拠レベルを超えて必要な関数がサポートされているかどうかを判断する**SQLGetFunctions、** および**SQLGetTypeInfo**でサポートされる SQL データ型を決定できます。  
  
 アプリケーションは、ステートメント属性または接続属性を、その属性を指定して**SQLSetStmtAttr**または**SQLSetConnectAttr を**呼び出すことによってサポートされているかどうかを判断できます。 関数がSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返す場合、属性はサポートされます。SQL_ERRORおよび SQLSTATE HYC00 (オプション機能が実装されていない) を戻す場合、属性はサポートされません。  
  
 アプリケーションは **、SQLDrivers**を呼び出すことによって、ドライバーに接続する前に、限られた量の情報を決定することもできます。
