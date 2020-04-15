---
title: ODBC コンポーネントのインストール |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC]
- installing ODBC components [ODBC], about installing
- ODBC [ODBC], component installation
ms.assetid: b7e48e9c-8912-4003-b4ef-30aa44de06a7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbd0a6aeba8073ce14b08b8635396b1f231895fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298982"
---
# <a name="installing-odbc-components"></a>ODBC コンポーネントのインストール
> [!NOTE]  
>  WINDOWS XP および Windows Server 2003 以降では、ODBC が Windows のオペレーション システムに含まれています。 ODBC は、以前のバージョンの Windows にのみ明示的にインストールしてください。  
  
 このセクションでは、ODBC コンポーネントのインストールと削除の方法について説明します。 ドライバーの開発者は常に ODBC コンポーネント (ドライバー) をインストールするため、このセクションを読む必要があります。 アプリケーション開発者は、ODBC コンポーネントをアプリケーションに付属させる場合にのみ、このセクションを読む必要があります。 ODBC コンポーネントには、ドライバー マネージャー、ドライバー、変換プログラム、インストーラー DLL、カーソル ライブラリ、および関連ファイルが含まれます。 このセクションでは、ODBC アプリケーションは ODBC コンポーネントとは見なされません。  
  
> [!NOTE]  
>  このセクションは、Windows プラットフォームに固有のものです。 ODBC コンポーネントを他のプラットフォームにインストールする方法は、プラットフォームに固有です。  
  
 ODBC コンポーネントは、ファイル単位ではなく、コンポーネントごとにインストールおよび削除されます。 たとえば、トランスレータ自体と多数のデータ ファイルで構成されるトランスレータは、これらのファイルをグループとしてインストールおよび削除します。ファイル単位でインストールおよび削除することはできません。 この理由は、完全なコンポーネントのみがシステムに存在することを確認するためです。  
  
 コンポーネントのインストールと削除を行う目的で、以下は ODBC コンポーネントとして定義されています。  
  
-   **コア コンポーネント。** ドライバー マネージャー、カーソル ライブラリ、インストーラー DLL、およびその他の関連ファイルは、コア コンポーネントを構成し、インストールし、グループとして削除する必要があります。  
  
-   **ドライバー。** 各ドライバーは、個別のコンポーネントです。  
  
-   **翻訳。** 各トランスレータは個別のコンポーネントです。  
  
 ODBC 3.5 以降で Unicode がサポートされている場合は、OLE DB コンポーネントを ODBC で使用する場合に考慮する必要があります。 ODBC 用 OLE DB プロバイダの 1.1 バージョンは、ODBC 3.0 内の特定の Unicode 仕様に書き込まれました。 これらの仕様は ODBC 3.5 で変更されたため、ODBC 3.5 以降を使用する場合は、プロバイダのバージョン 1.5 以降が必要です。 このセクションでは、次のトピックを扱います。  
  
-   [インストール コンポーネント](../../../odbc/reference/install/installation-components.md)  
  
-   [使用状況のカウント](../../../odbc/reference/install/usage-counting.md)
