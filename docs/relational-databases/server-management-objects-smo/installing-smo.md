---
title: "SMO のインストール |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: sql
ms.prod_service: database-engine
ms.component: smo
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- installing SMO
- SMO [SQL Server], installing
- SQL Server Management Objects, installing
ms.assetid: 140e9971-4940-4866-89b9-5cec938e2a16
caps.latest.revision: "46"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5d758997c68328cd984befcf808721336c18ece4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
#<a name="installing-smo"></a>SMO のインストール

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

このページでは、SMO を使用するアプリケーションおよび SMO を使用するためのシステム要件をインストールする方法について説明します。

## <a name="smo-nuget-package"></a>SMO の NuGet パッケージ

以降で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2017 SMO として配布される、 [Microsoft.SqlServer.SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) NuGet パッケージの SMO でのアプリケーションを開発できるようにします。

これは、SharedManagementObjects.msi で、SQL Server の各リリースの SQL Feature Pack の一部としてリリースされていたに代わるものです。 SMO を使用するアプリケーションでは、代わりに、NuGet パッケージを更新する必要があり、アプリケーションを開発すると、バイナリがインストールされていることを確認する負担になります。

>>[!Important]
>>前述のように、[ファイルとバージョン番号](files-and-version-numbers.md) ページで、SMO アセンブリを GAC にインストールしないでください。 SMO のこれらのバージョンを使用しても他のアプリケーションで問題が発生そうでした (など[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Management Studio)。

##<a name="installing-the-package"></a>パッケージをインストールします。

参照してください[NuGet のクイック スタートで、パッケージを使用する](https://docs.microsoft.com/en-us/nuget/quickstart/use-a-package)手順と例についてをインストールすると、NuGet パッケージを使用します。 
  
## <a name="system-requirements"></a>システム要件
  
 SMO が必要です[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]4.0 を実行するにはのでそれを使用しているアプリケーションは、クライアント コンピューターがそのバージョンがあるか、以降がインストールされてことを確認する必要があります。
  
