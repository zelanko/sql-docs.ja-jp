---
title: "データの切り捨て (SSIS) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
caps.latest.revision: "37"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b81910c1b53898137153ac1abbe2cf9b7ac4924d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="data-truncation-ssis"></a>データの切り捨て (SSIS)
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
  
  
