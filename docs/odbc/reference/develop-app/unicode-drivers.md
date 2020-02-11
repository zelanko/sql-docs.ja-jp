---
title: Unicode ドライバー |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ca9b70ee6a96759e496b831f7c12dc3ee78419b7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087869"
---
# <a name="unicode-drivers"></a>Unicode ドライバー
ドライバーが Unicode ドライバーであるか ANSI ドライバーであるかは、データソースの性質によって異なります。 データソースで Unicode データがサポートされている場合、ドライバーは Unicode ドライバーである必要があります。 データソースで ANSI データのみがサポートされている場合、ドライバーは ANSI ドライバーのままである必要があります。  
  
 Unicode ドライバーは、ドライバーマネージャーによって Unicode ドライバーとして認識されるように**Sqlconnectw**をエクスポートする必要があります。  
  
 Unicode ドライバーは、unicode 関数 (サフィックスは*W*) を受け入れ、unicode データを格納する必要があります。 また、ANSI 関数を受け入れることもできますが、には必要ありません。 (ドライバーマネージャーは、サフィックスが付いた ANSI 関数呼び出しをドライバーに渡しません*が、サフィックス*のない ansi 関数呼び出しに変換してから、ドライバーに渡します)。  
  
 Unicode ドライバーは、アプリケーションのバインドに応じて、Unicode または ANSI のいずれかで結果セットを返すことができる必要があります。 アプリケーションが SQL_C_CHAR にバインドされている場合、Unicode ドライバーは SQL_WCHAR データを SQL_CHAR に変換する必要があります。 ドライバーマネージャーは、SQL_C_WCHAR を ANSI ドライバーの SQL_C_CHAR にマップしますが、Unicode ドライバーのマッピングは行われません。  
  
> [!NOTE]  
>  ドライバーの種類を決定するときに、ドライバーマネージャーは**SQLSetConnectAttr**を呼び出し、接続時に SQL_ATTR_ANSI_APP 属性を設定します。 アプリケーションが ANSI Api を使用している場合、SQL_ATTR_ANSI_APP は SQL_AA_TRUE に設定され、Unicode を使用している場合は SQL_AA_FALSE の値に設定されます。 この属性は、ドライバーがアプリケーションの種類に基づいて異なる動作を示すために使用されます。 属性をアプリケーションで直接設定することはできず、 **Sqlgetconnectattr**ではサポートされていません。 ドライバーが ANSI と Unicode の両方のアプリケーションで同じ動作をする場合は、この属性の SQL_ERROR を返します。 ドライバーが SQL_SUCCESS を返した場合、ドライバーマネージャーは接続プールを使用するときに、ANSI と Unicode の接続を分離します。
