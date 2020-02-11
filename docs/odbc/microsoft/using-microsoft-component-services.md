---
title: Microsoft コンポーネントサービスを使用する |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 91d6dcf0ca7f87d6ed510d582f7a7ba0f80e8c74
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088147"
---
# <a name="using-microsoft-component-services"></a>Microsoft コンポーネント サービスの使用
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用してください。  
  
 Microsoft Windows NT/Windows 2000 および Microsoft Windows 95/98 で、Oracle データベースがトランザクションコンポーネントサービス (Windows NT を使用している場合は MTS) で動作できるようにすることができます。 トランザクションをサポートするコンポーネントサービスで Oracle データベースを使用できるようにするには、システム管理者が V $ XATRANS $ という名前のビューを作成する必要があります。 このスクリプトを作成するには、Oracle によって提供されるスクリプトを実行する必要があります。 詳細については、コンポーネントサービスのヘルプまたは Oracle のドキュメントを参照してください。
