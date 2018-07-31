---
title: ICommand (OLE DB) |Microsoft Docs
description: ICommand インターフェイス (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ICommand [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 2627398879f7525ab8cd9182f2f1102500cfb5a5
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39106208"
---
# <a name="icommand-ole-db"></a>ICommand (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  この記事では、OLE DB、OLE DB Driver for SQL Server に固有の動作について説明します。  
  
## <a name="icommandexecute"></a>ICommand::Execute  
 列のサイズより大きなデータを挿入すると、通常はエラーが発生します。 ただし、S_OK が返され、*dwStatus* が DBSTATUS_S_TRUNCATED に設定される場合もあります。 一般的に発生、パラメーターを使用してデータを挿入するときに、列のデータを保持するのに十分な大きさと**icommandwithparameters::setparameterinfo**呼び出されていません。  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)
  
  
