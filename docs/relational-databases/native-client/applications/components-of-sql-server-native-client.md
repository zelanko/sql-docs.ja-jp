---
title: SQL Server Native Client のコンポーネント |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3829f6693968cc988cb7bb4df7a444f61e7ef342
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43101360"
---
# <a name="components-of-sql-server-native-client"></a>SQL Server Native Client のコンポーネント
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client には、次のコンポーネントが含まれています。  
  
|コンポーネント|説明|  
|---------------|-----------------|  
|sqlncli11.dll|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client のすべての機能を含む DLL (ダイナミック リンク ライブラリ) ファイル。 このファイルには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーが含まれます。|  
|sqlnclir11.rll|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ライブラリに付随するリソース ファイル。|   
|sqlncli.h|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を使用する場合に必要となる、新しいすべての定義を含む [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ヘッダー ファイル。 このヘッダー ファイルは、odbcss.h ヘッダー ファイルと sqloledb.h ヘッダー ファイルの両方に置き換わるものです。<br /><br /> 注: は、sqlncli.h と odbcss.h を同じプログラムで、を参照することはできませんが、sqloledb.h を最初に定義されている限り、sqlncli.h と sqloledb.h を同じプログラム内で参照できます。|  
|sqlncli11.lib|直接の呼び出しに必要なライブラリ ファイル、 **bcp**ユーティリティ関数の一部である、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー。<br /><br /> 注: プログラミング コードで sqlncli11.lib ファイルを参照する場合は必要があります sqlncli11.dll ファイルがシステム パス、およびを行うユーザーのシステム パスであるかどうかを確認するアプリケーションを使用します。|  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client を使用したアプリケーションのビルド](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
