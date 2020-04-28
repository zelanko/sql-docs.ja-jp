---
title: Null 値の許容と3つの値の論理比較 |Microsoft Docs
description: この記事では、.NET Framework 内の SqlTypes の型と SQL Server データ型の違いについて説明します。これには、セマンティクスと精度が似ています。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- precision [CLR integration]
- overflow detections [CLR integration]
- null values [CLR integration]
- three-value logic comparisons [CLR integration]
- data types [CLR integration]
- SqlBoolean data type
ms.assetid: 13da4c7f-1010-4b2d-a63c-c69b6bfd96f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f016abf2113afef3e02f01fd9842b91b742d50a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488463"
---
# <a name="nullability-and-three-value-logic-comparisons"></a>NULL 値の許容と 3 値論理比較
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型に慣れている場合は、の[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] **SqlTypes**名前空間に類似したセマンティクスと有効桁数があります。 ただし、いくつか違いもあります。このトピックでは、これらの違いの中から最も重要な点について説明します。  
  
## <a name="null-values"></a>NULL 値  
 CLR (共通言語ランタイム) のネイティブ データ型と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型の主な違いは、CLR データ型では NULL 値が許容されないのに対して、SQL Server データ型では完全な NULL セマンティクスが用意されているという点です。  
  
 比較は NULL 値の影響を受けます。 つまり、2 つの値 x と y を比較するときに、x または y が NULL の場合、一部の論理比較では true または false ではなく UNKNOWN 値に評価されます。  
  
## <a name="sqlboolean-data-type"></a>SqlBoolean データ型  
 **SqlTypes**名前空間は、この3つの値のロジックを表す**sqlboolean**型を導入します。 **SqlTypes**間の比較では、 **sqlboolean**値型が返されます。 不明な値は、 **Sqlboolean**型の null 値で表されます。 **Sqlboolean**型の値を確認するために、 **IsTrue**、 **IsFalse**、および**IsNull**の各プロパティが用意されています。  
  
## <a name="operations-functions-and-null-values"></a>演算、関数、および NULL 値  
 すべての算術演算子 (+、- \*、、/、%)、ビットごとの演算子 (~、&、および |) は、 **SqlTypes**のオペランドまたは引数のいずれかが null の場合に null を返します。 **IsNull**プロパティは常に true または false の値を返します。  
  
## <a name="precision"></a>Precision  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR の decimal データ型の最大値は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の numeric データ型や decimal データ型の最大値とは異なります。 また、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR の decimal データ型では、最大有効桁数が想定されます。 ただし、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]CLR では、 **sqldecimal**は同じ最大有効桁数と小数点以下桁数、およびの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]decimal データ型と同じセマンティクスを提供します。  
  
## <a name="overflow-detection"></a>オーバーフローの検出  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR では、非常に大きな 2 つの数を加算しても例外がスローされないことがあります。 チェック演算子を使用しないと、負の整数に "回り込んだ" 結果が返されます。 **SqlTypes**では、すべてのオーバーフローおよびアンダーフローエラーと0除算エラーに対して例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
