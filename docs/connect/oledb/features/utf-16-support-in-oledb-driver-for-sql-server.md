---
title: SQL Server の OLE DB ドライバーの utf-16 サポート |Microsoft ドキュメント
description: SQL Server の OLE DB ドライバーの utf-16 のサポート
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 3882e5b5116af5866410be0b309b54eb48e91902
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="utf-16-support-in-ole-db-driver-for-sql-server"></a>SQL Server の OLE DB ドライバーの utf-16 のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  以降で[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]場合、列の結果または出力パラメーターをバインドするときに、固定長バッファーを指定した場合、 **wchar**終端文字が上位サロゲート コード ポイントの前に、バッファーに書き込まれた文字、サロゲート ペア、および場合は、次へ**wchar**文字が下位サロゲート コード ポイントで、OLE DB Driver for SQL Server は、バッファーに上位サロゲート コード ポイントを追加しません。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server の機能](../../oledb/features/oledb-driver-for-sql-server-features.md)   
  
  
