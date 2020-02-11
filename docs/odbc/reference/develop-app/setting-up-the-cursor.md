---
title: カーソルの設定 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: b80afb0e-ef2f-408f-86f5-a392edd99a56
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c47e534f069f810948189f2668d4ecdfbfa4ad79
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107543"
---
# <a name="setting-up-the-cursor"></a>カーソルの設定
アプリケーションでは、結果セットを作成するステートメントを実行する前に、カーソルの種類を指定できます。 これは、SQL_ATTR_CURSOR_TYPE statement 属性を使用して行われます。 アプリケーションで型が明示的に指定されていない場合は、順方向専用カーソルが使用されます。 混合カーソルを取得するには、アプリケーションでキーセットドリブンカーソルを指定しますが、結果セットのサイズよりも小さいキーセットのサイズを宣言します。  
  
 キーセットドリブンカーソルおよび混合カーソルの場合は、アプリケーションでキーセットのサイズを指定することもできます。 これは、SQL_ATTR_KEYSET_SIZE statement 属性を使用して行われます。 キーセットのサイズが既定値の0に設定されている場合、キーセットのサイズは結果セットのサイズに設定され、キーセットドリブンカーソルが使用されます。 キーセットのサイズは、カーソルを開いた後に変更できます。  
  
 アプリケーションでは、行セットのサイズを設定することもできます。詳細については、このセクションの「[ブロックカーソルの使用](../../../odbc/reference/develop-app/using-block-cursors.md)」を参照してください。
