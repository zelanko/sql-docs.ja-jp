---
title: NULL 値許容度と 3 値論理比較 |マイクロソフトドキュメント
description: この記事では、セマンティクスと精度が似ている .NET Framework の System.Data.SqlTypes の型と SQL Server データ型がどのように異なるかについて説明します。
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
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488463"
---
# <a name="nullability-and-three-value-logic-comparisons"></a>NULL 値の許容と 3 値論理比較
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  データ型に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]精通している場合は **、System.Data.SqlTypes**名前空間の同様のセマンティクスと精度が[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]見つかるとします。 ただし、いくつか違いもあります。このトピックでは、これらの違いの中から最も重要な点について説明します。  
  
## <a name="null-values"></a>NULL 値  
 CLR (共通言語ランタイム) のネイティブ データ型と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型の主な違いは、CLR データ型では NULL 値が許容されないのに対して、SQL Server データ型では完全な NULL セマンティクスが用意されているという点です。  
  
 比較は NULL 値の影響を受けます。 つまり、2 つの値 x と y を比較するときに、x または y が NULL の場合、一部の論理比較では true または false ではなく UNKNOWN 値に評価されます。  
  
## <a name="sqlboolean-data-type"></a>SqlBoolean データ型  
 名前空間**では**、この 3 値ロジックを表す**SqlBoolean**型が導入されています。 任意の**SqlType の**比較は、**値型を返**します。 不明な値は **、SqlBoolean**型の null 値で表されます。 プロパティ**は****、SqlBoolean**型の値をチェックするために**提供されます。** **IsFalse**  
  
## <a name="operations-functions-and-null-values"></a>演算、関数、および NULL 値  
 算術演算子 (+、-、、/、%)、\*ビットごとの演算子 (~、&、および |) のすべての算術演算子、および**SqlTypes**のオペランドまたは引数のいずれかが NULL の場合、ほとんどの関数は NULL を返します。 **IsNull**プロパティは、常に真または偽の値を返します。  
  
## <a name="precision"></a>Precision  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR の decimal データ型の最大値は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の numeric データ型や decimal データ型の最大値とは異なります。 また、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR の decimal データ型では、最大有効桁数が想定されます。 ただし、 CLR[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、 **SqlDecimal**は、最大精度と小数点以下桁数と同じ意味を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]提供します。  
  
## <a name="overflow-detection"></a>オーバーフローの検出  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR では、非常に大きな 2 つの数を加算しても例外がスローされないことがあります。 チェック演算子を使用しないと、負の整数に "回り込んだ" 結果が返されます。 **System.Data.SqlTypes**では、オーバーフローエラーとアンダーフロー エラー、およびゼロ除算エラーの例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
