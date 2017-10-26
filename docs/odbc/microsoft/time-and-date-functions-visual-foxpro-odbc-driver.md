---
title: "時刻および日付関数 (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC date functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], time and date functions
- FoxPro ODBC driver [ODBC], time and date functions
- time and date functions [ODBC]
- ODBC time and date functions [ODBC]
- date functions [ODBC]
ms.assetid: c1fb63b7-af50-45d6-8dec-ae6ea7119527
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bab52b29d54416dca84d18cb0cd2b832da1b4d63
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="time-and-date-functions-visual-foxpro-odbc-driver"></a>時刻および日付関数 (Visual FoxPro ODBC ドライバー)
次の表に、Visual FoxPro ODBC ドライバーでサポートされている ODBC の日付と時刻関数同じ関数の場合、Visual FoxPro 文法は、ODBC 構文によって異なります、同等の Visual FoxPro が一覧表示されます。  
  
|ODBC の文法|Visual FoxPro 文法|  
|------------------|---------------------------|  
|CURDATE*に関するページ)*|日付*)*|  
|CURTIME*に関するページ)*|時間*に関するページ)*|  
|DAYNAME*(date_exp)*|CDOW*(date_exp)*|  
|DAYOFMONTH (*date_exp)*|1 日*に関するページ)*|  
|時間*(time_exp)*||  
|分*(time_exp)*||  
|月*(time_exp)*||  
|MONTHNAME*(date_exp)*|CMONTH*(date_exp)*|  
|今すぐ*)*|DATETIME*)*|  
|2 番目*(time_exp)*|1 秒*(time_exp)*|  
|週*(date_exp)*||  
|年*(date_exp)*||  
  
 次の日付と時刻の関数はサポートされていません。  
  
 DAYOFYEAR *(date_exp)*  
  
 四半期*(date_exp)*  
  
 TIMESTAMPADD *(間隔、integer_exp、timestamp_exp)*  
  
 TIMESTAMPDIFF *(間隔、timestamp_exp1、timestamp_exp2)*  
  
## <a name="odbc-escape-sequences"></a>ODBC エスケープ シーケンス  
 ドライバーでは、日付とタイムスタンプのデータの ODBC エスケープ シーケンスもサポートします。 エスケープ句の構文は次のとおりです。  
  
```  
--(*vendor(Microsoft),product(ODBC) d 'value' *)—  
--(*vendor(Microsoft),product(ODBC) ts ''value' *)—  
```  
  
 この構文で**d**ことを示します*値*の日付、 *yyyy mm dd*形式と**ts**ことを示します*値*タイムスタンプには、 *- yyyy-mm-dd hh:mm:ss*[.*f.*] 形式です。 日付とタイムスタンプのデータの略式の構文は次のとおりです。  
  
```  
{d 'value'}  
{ts 'value'}  
```  
  
 たとえば、次のステートメントの更新プログラムの ALLTYPES の表に、サポートされている SQL の UPDATE コマンドの日付とタイムスタンプ略式の構文を使用しています。  
  
```  
UPDATE alltypes  
   SET DAT_COL={d'1968-04-28'}  
   WHERE KEY=111  
  
UPDATE alltypes  
   SET DTI_COL={ts'1968-04-28 12:00:00'}  
   WHERE KEY=111  
```  
  
## <a name="remarks"></a>解説  
 エスケープ シーケンスの詳細については、次を参照してください。 [odbc エスケープ シーケンス](../../odbc/reference/develop-app/escape-sequences-in-odbc.md)で、 *ODBC プログラマ リファレンス*です。

