---
title: ODBC コンポーネントのインストール |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC]
- installing ODBC components [ODBC], about installing
- ODBC [ODBC], component installation
ms.assetid: b7e48e9c-8912-4003-b4ef-30aa44de06a7
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9204ecc8cc98f8a26cfad5414864789b8d7a351b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="installing-odbc-components"></a>ODBC コンポーネントのインストール
> [!NOTE]  
>  Windows XP および Windows Server 2003 以降、Windows オペレーティング システムに ODBC が含まれます。 以前のバージョンの Windows で ODBC を明示的にのみインストールしてください。  
  
 このセクションでは、ODBC コンポーネントをインストールおよび削除する方法について説明します。 ドライバーの開発者は、常に ODBC コンポーネント (ドライバー) をインストールするため、このセクションの内容を読み取り、必要があります。 アプリケーション開発者は、ODBC コンポーネントとアプリケーションを提供する場合にのみ、このセクションの内容を読み取る必要があります。 ODBC コンポーネントには、ドライバー マネージャー、ドライバー、翻訳、インストーラー DLL、カーソル ライブラリと、関連ファイルが含まれます。 このセクションの目的で、ODBC アプリケーションは、ODBC コンポーネントには考慮されません。  
  
> [!NOTE]  
>  このセクションでは、Microsoft Windows プラットフォームに固有です。 他のプラットフォームでの ODBC コンポーネントのインストール方法と、プラットフォーム固有です。  
  
 ODBC コンポーネントがインストールされ、ファイルごとではなく、コンポーネントによってごとに削除します。 たとえば、トランスレーターがの場合は、変換プログラム自体とデータ ファイルの数、これらのファイルがインストールされ、グループとして削除必要がありますいないしておく必要がファイルごとに削除します。 その理由は、システムにのみ完全なコンポーネントが存在するかどうかを確認を開始します。  
  
 インストールおよびコンポーネントを削除するために、次は定義 ODBC コンポーネントであるします。  
  
-   **コア コンポーネント。** ドライバー マネージャー、カーソル ライブラリ、インストーラー DLL、およびその他の関連するファイルのコア コンポーネントを構成してする必要がありますをインストールし、グループとして削除します。  
  
-   **ドライバーです。** 各ドライバーは、別のコンポーネントです。  
  
-   **翻訳者です。** 各翻訳は、別のコンポーネントです。  
  
 Unicode ODBC 3.5 以降をサポートすると、ODBC と OLE DB コンポーネントを使用するいくつか考慮の対象を指定してください。 OLE DB Provider for ODBC のバージョン 1.1 は、ODBC 3.0 内の特定の Unicode 仕様に作成されました。 ODBC 3.5 ではこれらの仕様が変更されたためには、ODBC 3.5 を使用する場合は、バージョン 1.5 またはそれ以降のプロバイダーを設定する必要以降。 このセクションでは、次のトピックを扱います。  
  
-   [インストール コンポーネント](../../../odbc/reference/install/installation-components.md)  
  
-   [使用状況のカウント](../../../odbc/reference/install/usage-counting.md)
