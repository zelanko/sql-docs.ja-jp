---
title: DQS ドメインに対してサポートされる SQL Server のデータ型と SSIS のデータ型 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 4931143a-b84d-478b-9b45-174128d36ed3
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 06e593c676c206f863bdb110be5c93e5003b4e13
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65484096"
---
# <a name="supported-sql-server-and-ssis-data-types-for-dqs-domains"></a>DQS ドメインに対してサポートされる SQL Server のデータ型と SSIS のデータ型
  SQL Server と SQL Server Integration Services (SSIS) にはさまざまなデータ型が存在しますが、DQS ドメインのデータ型は Date、Decimal、Integer、String の 4 つだけです。 SQL Server と SSIS のデータ型には、DQS でサポートされないものも存在します。 ソース データを DQS ドメインにマッピングし、データ品質アクティビティを実行できるのは、ソースのデータ型が DQS でサポートされていて、なおかつ DQS ドメインのデータ型と一致する場合だけです。 このトピックでは、SQL Server と SSIS のデータ型のうち、DQS ドメインの 4 つのデータ型にそれぞれマッピングできる、サポートされるデータ型について取り上げます。  
  
> [!NOTE]  
>  .xlsx および .xls ファイルでは、ソース列のデータ型は最初の 8 行で最も多く使用されているデータ型によって決定されます。 セルがそのデータ型に従っていない場合、セルの値は null になります。 同様に、.csv ファイルでは、ソース列のデータ型は最初の 8 行で最も多く使用されているデータ型によって決定されます。  
  
##  <a name="supported-sql-server-data-types"></a><a name="SQLServer"></a>サポートされている SQL Server データ型  
 次の表は、DQS ドメインの各データ型について、サポートされる SQL Server のデータ型を示しています。  
  
|DQS ドメインのデータ型|サポートされる SQL Server のデータ型|  
|--------------------------|------------------------------------|  
|日付|日付|  
|Decimal|decimal<br /><br /> float<br /><br /> money<br /><br /> numeric<br /><br /> real<br /><br /> smallmoney|  
|Integer|bigint<br /><br /> INT<br /><br /> smallint<br /><br /> tinyint|  
|String|char<br /><br /> nchar<br /><br /> nvarchar<br /><br /> varchar|  
  
 その他の SQL Server データ型は、DQS ではサポートされません。 SQL Server データ型については、「[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)」をご覧ください。  
  
##  <a name="supported-ssis-data-types"></a><a name="SSIS"></a>サポートされる SSIS のデータ型  
 次の表は、DQS ドメインの各データ型について、サポートされる SSIS のデータ型を示しています。  
  
|DQS ドメインのデータ型|サポートされる SSIS のデータ型|  
|--------------------------|------------------------------|  
|日付|DT_DATE|  
|Decimal|DT_DECIMAL<br /><br /> DT_NUMERIC<br /><br /> DT_R4<br /><br /> DT_R8|  
|Integer|DT_I1<br /><br /> DT_I2<br /><br /> DT_I4<br /><br /> DT_I8<br /><br /> DT_U1<br /><br /> DT_U2<br /><br /> DT_U4<br /><br /> DT_U8|  
|String|DT_STR<br /><br /> DT_WSTR|  
  
 その他の SSIS データ型は、DQS ではサポートされません。 SSIS のすべてのデータ型については、「 [Integration Services Data Types](../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ドメインの管理](../../2014/data-quality-services/managing-a-domain.md)  
  
  
