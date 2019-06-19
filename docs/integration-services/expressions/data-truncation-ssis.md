---
title: データの切り捨て (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7417f763aaff5d541f351848eb59b71e9a67a70f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65725532"
---
# <a name="data-truncation-ssis"></a>データの切り捨て (SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  あるデータ型から別のデータ型に値を変換すると、値が切り詰められる場合があります。  
  
 切り詰めは、次の場合に発生します。  
  
-   文字列データを *DT_WSTR* から同じ長さの *DT_STR* に変換するとき、元の文字列に 2 バイト文字が含まれている場合に発生することがあります。  
  
-   整数を *DT_I4* から *DT_I2* にキャストすると有効数字が失われる場合があります。  
  
-   符号なし整数を符号付き整数にキャストすると有効数字が失われる場合があります。  
  
-   実数を *DT_R8* から *DT_R4* にキャストすると有効ではない数字が失われる場合があります。  
  
-   整数を *DT_I4* から *DT_R4* にキャストすると有効ではない数字が失われる場合があります。  
  
 式エバリュエーターは切り捨てが発生する可能性のある明示的なキャストを識別し、式が解析されるときに警告を発生します。 たとえば、30 文字の文字列が 20 文字の文字列にキャストされる場合、式エバリュエーターで警告が発生します。  
  
 ただし、切り詰めは実行時にチェックされません。 実行時、データは警告なしに切り詰められます。 ただし、ほとんどのデータ アダプターおよび変換では、エラー行を処理できるエラー出力がサポートされています。  
  
 データの切り詰め処理の詳細については、「 [データのエラー処理](../../integration-services/data-flow/error-handling-in-data.md)」を参照してください。  
  
  
