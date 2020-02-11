---
title: テーブル名の制限 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, table name limitations
- table name limitations [ODBC]
- Excel driver [ODBC], table name limitations
ms.assetid: d9843e4b-1d05-4d5a-9dc3-ee9ec59edb97
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 152a0aa1e8d92424b2f60c49f44888de7d3e528c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67939776"
---
# <a name="table-name-limitations"></a>テーブル名の制限
テーブル名には、任意の有効な文字 (たとえば、スペース) を含めることができます。 テーブル名に文字、数字、およびアンダースコア以外の文字が含まれている場合は、名前を引用符 (') で囲むことによって区切る必要があります。  
  
 Microsoft Excel driver が使用され、テーブル名がデータベース参照によって修飾されていない場合、既定のデータベースは暗黙的に指定されます。 Microsoft Excel の名前に "!" 文字が含まれている場合は、代わりに "$" 文字に自動的に変換されます。  
  
 ファイル名> を参照\<する microsoft excel テーブル名は、microsoft excel 3.0 および4.0 ファイルでサポートされています。 ブック名> を参照\<する microsoft excel テーブル名は、microsoft excel 5.0、7.0、または97ファイルでサポートされています。  
  
 DBASE ドライバーを使用すると、ASCII 値が127より大きい文字はアンダースコアに変換されます。  
  
 Microsoft Access ドライバーを使用する場合、テーブル名は64文字に制限されます。  
  
 DBASE、Microsoft Excel 3.0 または4.0、Paradox、またはテキストドライバーを使用する場合、特殊な MS-DOS キーワード CON、AUX、LPT1、および LPT2 をテーブル名として使用することはできません。
