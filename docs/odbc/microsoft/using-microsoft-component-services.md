---
title: マイクロソフト コンポーネント サービスの使用 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], component services
- component services [ODBC]
ms.assetid: 06450562-d8f3-4987-b7bd-4a70223ff937
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fb5763058fa198cbad7464434e31942ef8d6cd7d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307583"
---
# <a name="using-microsoft-component-services"></a>Microsoft コンポーネント サービスの使用
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle データベースは、Windows NT/Windows 2000 および Windows 95/98 のトランザクション コンポーネント サービス (Windows NT を使用している場合は MTS) を使用して動作するように設定できます。 Oracle データベースがトランザクションをサポートするコンポーネント サービスと連携できるようにするには、システム管理者が V$XATRANS$ という名前のビューを作成する必要があります。 このスクリプトを作成するには、Oracle 提供のスクリプトを実行する必要があります。 詳細については、コンポーネント・サービスのヘルプまたは Oracle のマニュアルを参照してください。
