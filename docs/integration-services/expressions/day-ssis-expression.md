---
title: "DAY (SSIS 式) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DAY 関数"
  - "日付 [Integration Services], DAY"
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# DAY (SSIS 式)
  ある日付の、日の日付要素を表す整数値を返します。  
  
## 構文  
  
```  
  
DAY(date)  
```  
  
## 引数  
 *date*  
 有効な日付または日付形式の文字列を返す式です。  
  
## 戻り値の型  
 DT_I4  
  
## 解説  
 引数が NULL の場合、DAY は NULL を返します。  
  
 日付リテラルは、日付データ型のいずれかに明示的にキャストされる必要があります。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
> [!NOTE]  
>  日付リテラルが DT_DBTIMESTAMPOFFSET と DT_DBTIMESTAMP2 のいずれかの日付データ型に明示的にキャストされると、式の検証は失敗します。  
  
 DAY 関数を使用すると、DATEPART("DAY", date) 関数を使用する場合と同じ結果を、より簡単に取得できます。  
  
## 式の例  
 この例は、日付リテラルの日数を返します。 データ形式が "mm/dd/yyyy" 形式の場合、この例は 23 を返します。  
  
```  
DAY((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 この例は、**ModifiedDate** 列内の日を表す整数を返します。  
  
```  
DAY(ModifiedDate)  
```  
  
 この例は、現在の日付の日を表す整数を返します。  
  
```  
DAY(GETDATE())  
```  
  
## 参照  
 [DATEADD &#40;SSIS 式&#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF &#40;SSIS 式&#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART &#40;SSIS 式&#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [MONTH &#40;SSIS 式&#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [YEAR &#40;SSIS 式&#41;](../../integration-services/expressions/year-ssis-expression.md)   
 [関数 &#40;SSIS 式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  