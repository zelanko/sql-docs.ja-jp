---
title: データの切り捨て (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e0c4280c9eacd22ebf84bf1570d485de51cab09b
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428969"
---
# <a name="data-truncation-ssis"></a>データの切り捨て (SSIS)
  式により誤ってデータが切り捨てられる場合があります。 データの切り捨ては次の環境で発生する可能性があります。  
  
-   文字列。 たとえば、DT_WSTR データ型の文字列データを、文字長単位で同じ長さの文字列に変換する場合、DT_STR データ型に変換すると、元の文字列に 2 バイト文字が含まれている場合にデータが失われます。  
  
-   有効桁。 たとえば、整数値を DT_I4 データ型から DT_I2 データ型にキャストする場合、または符号なし整数を符号付き整数にキャストする場合などです。  
  
-   有効桁以外の桁。 たとえば、実数を DT_R8 データ型から DT_R4 データ型にキャストする場合、または整数を DT_I4 データ型から DT_R4 データ型にキャストする場合などです。  
  
 式エバリュエーターは切り捨てが発生する可能性のある明示的なキャストを識別し、式が解析されるときに警告を発生します。 たとえば、30 文字の文字列が 20 文字の文字列にキャストされる場合、式エバリュエーターで警告が発生します。  
  
> [!NOTE]  
>  切り捨ては実行時にはチェックされません。データは警告なしで切り捨てられます。 ただし、ほとんどのデータ アダプターおよび変換では、エラー行の処理を実行できるエラー出力がサポートされています。 データの切り捨て処理の詳細については、「[データのエラー処理](../data-flow/error-handling-in-data.md)」を参照してください。  
  
  
