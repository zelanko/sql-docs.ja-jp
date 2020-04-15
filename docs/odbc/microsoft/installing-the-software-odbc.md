---
title: ソフトウェアのインストール (ODBC) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], installing
- installing ODBC driver for Oracle [ODBC]
ms.assetid: dfac8ade-eebe-4ebe-a199-feb740ed5bae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9bddfd9947017cc94214e57948e495b06cccc1cb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299982"
---
# <a name="installing-the-software-odbc"></a>インストール (ODBC)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle 用 ODBC ドライバーは、データ アクセス コンポーネントの 1 つです。 ODBC データ ソース アドミニストレータなどの他の ODBC コンポーネントに付属しており、既にインストールされている必要があります。 ドライバは[、www.microsoft.com](https://www.microsoft.com)のマイクロソフト製品サポート サービス オンライン Web サイトの「ドライバとその他のダウンロード」にも記載されています。  
  
 ネットワーク ソフトウェアは、独自のドキュメントに従ってインストールする必要があります。 Oracle 用 ODBC ドライバーは、ネットワーク ソフトウェアがサポートされている限り、インストールに関する特別な考慮事項は必要ありません。  
  
 Oracleソフトウェアは、独自のマニュアルに従ってインストールする必要があります。 Oracle 用 ODBC ドライバーは、一般に、ドライバーがバージョンをサポートしている限り、インストールに関する特別な考慮事項は必要ありません。 ただし、製品の互換性を維持するには、最新バージョンのドライバーを使用できるように、Oracle 用 ODBC ドライバーを最後にインストールします。 Oracle は、パブリシング FTP サイトを維持し、とりわけ、Oracle サーバー製品およびサーバー製品に付属するクライアント コンポーネントにパッチを投稿します。 これらの修正プログラムは、いくつかのマイクロソフト製品およびテクノロジが適切に機能するために必要です。 このサイトの詳細については[、Oracle ソフトウェア パッチを](../../odbc/microsoft/oracle-software-patches.md)参照してください。  
  
> [!CAUTION]  
>  MDAC/Windows DAC を介して Oracle ソフトウェアをインストールすると、MDAC の現在のバージョンが上書きされる場合があります。 ODBC コンポーネントを使用して問題が発生した場合は、MDAC を再インストールします。
