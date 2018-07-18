---
title: SMO のインストール |Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.prod_service: database-engine
ms.component: smo
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- installing SMO
- SMO [SQL Server], installing
- SQL Server Management Objects, installing
ms.assetid: 140e9971-4940-4866-89b9-5cec938e2a16
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8780920f4b535c77b82f404e84917d4cc97af4e1
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983884"
---
#<a name="installing-smo"></a>SMO のインストール

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

このページでは、アプリケーションと SMO を使用するためのシステム要件で使用するための SMO をインストールする方法について説明します。

## <a name="smo-nuget-package"></a>SMO の NuGet パッケージ

以降で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2017 SMO はで配布されて、 [Microsoft.SqlServer.SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) SMO でアプリケーションを開発できるようにする NuGet パッケージ。

これは、SharedManagementObjects.msi で、SQL Server の各リリースの SQL の Feature Pack の一部としてリリースされていたに代わるものです。 SMO を使用するアプリケーションでは、代わりに、NuGet パッケージを更新する必要があり、アプリケーションを開発すると、バイナリがインストールされていることを確認する負担になります。

>>[!Important]
>>説明したように、[ファイルとバージョン番号](files-and-version-numbers.md) ページで、SMO アセンブリを GAC にインストールしないでください。 SMO のこれらのバージョンを使用しても他のアプリケーションで問題を引き起こすそうでした (など[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Management Studio)。

##<a name="installing-the-package"></a>パッケージをインストールします。

参照してください[NuGet クイック スタート - パッケージを使用して](https://docs.microsoft.com/nuget/quickstart/use-a-package)手順と例についてをインストールすると、NuGet パッケージを使用します。 
  
## <a name="system-requirements"></a>システム要件
  
 SMO が必要です[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]4.0 を使用して任意のアプリケーションは、クライアント コンピューターがそのバージョンがあること、または以降がインストールされていることを確認する必要がありますので、実行します。
  
