---
title: データ型 (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], data types
- data types [SQL Server], extended stored procedures
ms.assetid: 37fb86b9-8819-4387-bcdc-9616968e15ad
author: rothja
ms.author: jroth
ms.openlocfilehash: b510e74d507cb540fa617b6c0da48c3090429192
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85679056"
---
# <a name="data-types-extended-stored-procedure-api"></a>データ型 (拡張ストアド プロシージャ API)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 拡張ストアド プロシージャ API のデータ型を使用するには、プログラムに Srv.h ヘッダー ファイルをインクルードします。  
  
|データの種類|SQL Server のデータ型|説明|  
|---------------|--------------------------|-----------------|  
|SRVBIGBINARY|**[バイナリ]**|**binary** データ型。長さは 0 から 8,000 バイトです。|  
|SRVBIGCHAR|**char**|**character** データ型。長さは 0 から 8,000 バイトです。|  
|SRVBIGVARBINARY|**varbinary**|可変長 **binary** データ型。長さは 0 から 8,000 バイトです。|  
|SRVBIGVARCHAR|**varchar**|可変長 **character** データ型。長さは 0 から 8,000 バイトです。|  
|SRVBINARY|**[バイナリ]**|**binary**データ型。|  
|SRVBIT|**ビット**|**bit** データ型。|  
|SRVBITN|**bit null**|**bit** データ型。NULL 値を許容します。|  
|SRVCHAR|**char**|**character** データ型。|  
|SRVDATETIME|**datetime**|8 バイトの **datetime** データ型。|  
|SRVDATETIM4|**smalldatetime**|4 バイトの **smalldatetime** データ型。|  
|SRVDATETIMN|**datetime null**|**smalldatetime** または **datetime** データ型。NULL 値を許容します。|  
|SRVDECIMAL|**decimal**|**decimal**データ型。|  
|SRVDECIMALN|**decimal null**|**decimal** データ型。NULL 値を許容します。|  
|SRVFLT4|**real**|4 バイトの **real** データ型。|  
|SRVFLT8|**float**|8 バイトの **float** データ型。|  
|SRVFLTN|**real** &#124; **float null**|**real** または **float** データ型。NULL 値を許容します。|  
|SRVIMAGE|**イメージ**|**image** データ型。|  
|SRVINT1|**tinyint**|1 バイトの **tinyint** データ型。|  
|SRVINT2|**smallint**|2 バイトの **smallint** データ型。|  
|SRVINT4|**int**|4 バイトの **int** データ型。|  
|SRVINTN|**tinyint** &#124; **smallint** &#124; **int null**|**tinyint**、**smallint**、または **int** データ型。NULL 値を許容します。|  
|SRVMONEY4|**smallmoney**|4 バイトの **smallmoney** データ型。|  
|SRVMONEY|**money**|8 バイトの **money** データ型。|  
|SRVMONEYN|**money** &#124; **smallmoney null**|**smallmoney** または **money** データ型。NULL 値を許容します。|  
|SRVNCHAR|**nchar**|Unicode の **character** データ型。|  
|SRVNTEXT|**ntext**|Unicode の **text** データ型。|  
|SRVNUMERIC|**numeric**|**numeric** データ型。|  
|SRVNUMERICN|**numeric null**|**numeric** データ型。NULL 値を許容します。|  
|SRVNVARCHAR|**nvarchar**|Unicode の可変長の **character** データ型。|  
|SRVTEXT|**text**|**text** データ型。|  
|SRVVARBINARY|**varbinary**|可変長の **binary** データ型。|  
|SRVVARCHAR|**varchar**|可変長の **character** データ型。|  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。  
  
  
