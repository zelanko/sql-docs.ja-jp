---
description: SQLState プロパティ
title: SQLState プロパティ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetSQLState
- Error::SQLState
- Error::get_SQLState
helpviewer_keywords:
- SQLState property
ms.assetid: f9e25967-54b0-444d-af2a-0d2c75365d3e
author: rothja
ms.author: jroth
ms.openlocfilehash: 4216b6ce215db761c95bb830f7fdf26a05174b40
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442014"
---
# <a name="sqlstate-property"></a>SQLState プロパティ
指定された [エラー](../../../ado/reference/ado-api/error-object.md) オブジェクトの SQL 状態を示します。  
  
## <a name="return-value"></a>戻り値  
 は、ANSI SQL 標準に従った5文字の **文字列** 値を返し、エラーコードを示します。  
  
## <a name="remarks"></a>解説  
 SQL ステートメントの処理中にエラーが発生した場合にプロバイダーが返す5文字のエラーコードを読み取るには、 **SQLState** プロパティを使用します。 たとえば、Microsoft SQL Server データベースを使用して Microsoft OLE DB Provider for ODBC を使用すると、odbc からの SQL 状態エラーコードが生成されます。これは、ODBC に固有のエラーや、Microsoft SQL Server から発生したエラーに基づいて行われ、ODBC エラーにマップされます。 これらのエラーコードは ANSI SQL 標準に記載されていますが、データソースによって実装方法が異なる場合があります。  
  
## <a name="applies-to"></a>適用対象  
 [Error オブジェクト](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>参照  
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
