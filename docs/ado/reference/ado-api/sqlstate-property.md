---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e43ace17f3f2b709c327f185a189a107b6b73065
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67916884"
---
# <a name="sqlstate-property"></a>SQLState プロパティ
指定された[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクトの SQL 状態を示します。  
  
## <a name="return-value"></a>戻り値  
 は、ANSI SQL 標準に従った5文字の**文字列**値を返し、エラーコードを示します。  
  
## <a name="remarks"></a>解説  
 SQL ステートメントの処理中にエラーが発生した場合にプロバイダーが返す5文字のエラーコードを読み取るには、 **SQLState**プロパティを使用します。 たとえば、Microsoft SQL Server データベースを使用して Microsoft OLE DB Provider for ODBC を使用すると、odbc からの SQL 状態エラーコードが生成されます。これは、ODBC に固有のエラーまたは Microsoft SQL Server から発生したエラーに基づいて行われ、ODBC にマップされます。誤り. これらのエラーコードは ANSI SQL 標準に記載されていますが、データソースによって実装方法が異なる場合があります。  
  
## <a name="applies-to"></a>適用対象  
 [Error オブジェクト](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>参照  
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description、HelpContext、HelpFile、のエラー、Number、Source、および SQLState プロパティの例 (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
