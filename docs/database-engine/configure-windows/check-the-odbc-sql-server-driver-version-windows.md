---
title: ODBC SQL Server のドライバーのバージョンを確認する方法 (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 11/07/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- driver version number [ODBC]
- ODBC drivers, version number
ms.assetid: 43451080-a562-4231-b1d4-1ba35ca0ea79
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c7e602687a8f677af5a3160a7e3e1c5b0c2f900d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32863417"
---
# <a name="check-the-odbc-sql-server-driver-version-windows"></a>ODBC SQL Server のドライバーのバージョンを確認する方法 (Windows)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  コンピューターによっては、[!INCLUDE[msCoName](../../includes/msconame-md.md)] や他社製のさまざまな ODBC ドライバーが組み込まれています。 このトピックでは、Windows の **ODBC データ ソース アドミニストレーター** を使用して、インストールされている ODBC ドライバーのバージョンを確認する方法について説明します。  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-check-the-odbc-sql-server-driver-version-32-bit-odbc"></a>ODBC SQL Server のドライバーのバージョンを確認するには (32 ビット ODBC)  
  
-   **ODBC データ ソース アドミニストレーター**で **[ドライバー]** タブをクリックします。  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [バージョン] **列に、Microsoft** エントリの情報が表示されます。  


> [!NOTE]  
>  SQL Database の Azure Active Directory 認証への接続には、 [ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339)などの最新ドライバーをインストールします。   

  
## <a name="see-also"></a>参照  
 [ODBC データ ソース アドミニストレーターの起動](../../database-engine/configure-windows/open-the-odbc-data-source-administrator.md)  
  
  
