---
title: 手順 1:ADO.NET 開発用に開発環境を構成する | Microsoft Docs
description: ADO.NET 開発用に環境を構成する方法について説明します。
ms.custom: ''
ms.date: 08/15/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9cba6a0d-5f21-49af-ac5a-17d199973590
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 2e9f0619f26abf8b077059c7e12c7fc34c51a2e6
ms.sourcegitcommit: 7eb80038c86acfef1d8e7bfd5f4e30e94aed3a75
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2020
ms.locfileid: "92081301"
---
# <a name="step-1-configure-development-environment-for-adonet-development"></a>手順 1:ADO.NET 開発用に開発環境を構成する

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

- 次の記事:&nbsp;&nbsp;&nbsp;[ステップ 2:ADO.NET 開発用の SQL データベースを作成する](step-2-create-sql-database-ado-net-development.md)  

## <a name="download-a-net-sql-driver"></a>.NET SQL ドライバーのダウンロード

現在のコード例では、Windows の場合に .NET Framework の ADO.NET を使用しています。 .NET Core は、(Windows に加えて) Linux と macOS でも利用できます。

### <a name="adonet-for-windows"></a>ADO.NET (Windows の場合)

- ![丸で囲まれたダウンロード矢印 (Framework)](../../ssms/media/download-icon.png)[.NET Framework をダウンロードする (ADO.NET](../sql-connection-libraries.md#anchor-20-drivers-relational-access) を含む)

- C# ソース コードを記述してコンパイルするために、Visual Studio Community または同様の統合開発環境 (IDE) をインストールします。 現在 Microsoft では、Visual Studio Community を *無料*で提供しています。  
    - [Visual Studio Community をダウンロードする](https://www.visualstudio.com/products/visual-studio-community-vs)  
    - [その他の無料版 Visual Studio の選択肢](https://www.visualstudio.com/products/free-developer-offers-vs.aspx)  


### <a name="net-core-for-linux-ubuntu-and-macos"></a>.NET Core (Linux-Ubuntu および macOS 用)

各種オペレーティング システム用の .NET Core をダウンロードするためのリンクは、以下にあります。

- ![丸で囲まれたダウンロード矢印 (Core)](../../ssms/media/download-icon.png)[.NET Core をダウンロードしてインストールする](../sql-connection-libraries.md#anchor-20-drivers-relational-access)
