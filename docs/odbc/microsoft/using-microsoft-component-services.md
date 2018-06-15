---
title: Microsoft コンポーネント サービスを使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], component services
- component services [ODBC]
ms.assetid: 06450562-d8f3-4987-b7bd-4a70223ff937
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a297d64708383edf997cbb6adf3b7d72aed53969
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32914427"
---
# <a name="using-microsoft-component-services"></a>Microsoft コンポーネント サービスを使用します。
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Microsoft Windows NT または Windows 2000 および Microsoft Windows 95/98 では、トランザクションのコンポーネント サービス (または Windows NT を使用している場合は MTS) を使用する Oracle データベースを有効にできます。 トランザクションをサポートするコンポーネント サービスを使用する Oracle データベースを有効にするには、システム管理者は、V$ XATRANS$ という名前のビューを作成する必要があります。 このスクリプトを作成するには、Oracle が指定したスクリプトを実行する必要があります。 詳細については、コンポーネント サービスのヘルプまたは Oracle のマニュアルを参照してください。
