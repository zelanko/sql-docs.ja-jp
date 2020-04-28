---
title: SMO | をインストールするMicrosoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.reviewer: ''
ms.prod_service: database-engine
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- installing SMO
- SMO [SQL Server], installing
- SQL Server Management Objects, installing
ms.assetid: 140e9971-4940-4866-89b9-5cec938e2a16
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cabd2d1ebbe726971e7837ff3e268ad3c2cee89f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "72041260"
---
# <a name="installing-smo"></a>SMO のインストール

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

このページでは、アプリケーションで使用する SMO をインストールする方法と、SMO を使用するためのシステム要件について説明します。

## <a name="smo-nuget-package"></a>SMO NuGet パッケージ

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 以降、Smo は[SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) NuGet パッケージとして配布され、ユーザーは smo を使用してアプリケーションを開発できるようになります。

これは、SQL Server の各リリースの SQL Feature Pack の一部としてリリースされた SharedManagementObjects の後継です。 SMO を使用するアプリケーションは、代わりに NuGet パッケージを使用するように更新する必要があり、開発中のアプリケーションと共にバイナリが確実にインストールされるようにします。

>>[!Important]
>>「[ファイルとバージョン番号](files-and-version-numbers.md)」ページで説明したように、SMO アセンブリを GAC にインストールすることはできません。 これを行うと、他のアプリケーションで問題が発生する可能性があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]これらのアプリケーションは、これらのバージョンの SMO (Management Studio など) も使用します。

## <a name="installing-the-package"></a>パッケージのインストール

Nuget パッケージのインストールと使用の手順と例については、「 [nuget クイックスタート-パッケージを使用](https://docs.microsoft.com/nuget/quickstart/use-a-package)する」を参照してください。 
  
## <a name="system-requirements"></a>システム要件
  
 SMO で[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]は、4.0 または .net Core 2.0 が実行されている必要があるため、これを使用するアプリケーションでは、クライアントコンピューターがそのバージョン以降をインストールしていることを確認する必要があります。 NetFx SMO ライブラリと共にインストールされる一部のネイティブバイナリでは、VC 2013 ランタイムもインストールする必要があります。このランタイムはパッケージに含まれていません。 ターゲットアーキテクチャに適した再頒布可能ファイルは、https://www.microsoft.com/download/details.aspx?id=40784
  
