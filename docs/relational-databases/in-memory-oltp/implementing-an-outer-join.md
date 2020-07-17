---
title: メモリ内 OUTER JOIN | Microsoft Docs
description: LEFT と RIGHT OUTER JOIN について説明します。 ネイティブ コンパイル T-SQL モジュールでは、SQL Server の LEFT および RIGHT OUTER JOIN がサポートされています。
ms.custom: ''
ms.date: 06/01/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 67084043-6b23-4975-b9db-6e49923d4bab
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1d9212c1e8d139f6b0d90658d0500700184123be
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723189"
---
# <a name="implementing-an-outer-join"></a>外部結合の実装

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  LEFT OUTER JOIN と RIGHT OUTER JOIN は、 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降のネイティブ コンパイル T-SQL モジュールでサポートされています。  
  
OUTER JOIN の詳細については、[FROM 句と JOIN、APPLY、PIVOT](../../t-sql/queries/from-transact-sql.md)に関するページを参照してください。
