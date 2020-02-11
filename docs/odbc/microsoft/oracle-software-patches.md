---
title: Oracle ソフトウェアパッチ |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], Oraclesoftware patches
- Oracle software patches [ODBC]
ms.assetid: 1275157b-f4e1-4c24-b273-c02555e261c2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fce38aabddfc3891314940d4b7cb21f02965c083
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68100777"
---
# <a name="oracle-software-patches"></a>Oracle ソフトウェアの修正プログラム
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用してください。  
  
 Microsoft ODBC Driver for Oracle、Microsoft OLE DB Provider for Oracle、インターネット情報など、いくつかの Microsoft 製品およびテクノロジが適切に機能するためには、Oracle サーバー製品とそのクライアントコンポーネント用の修正プログラムが必要です。サービス (IIS)、コンポーネントサービス (Windows NT を使用している場合は Microsoft トランザクションサーバー) など。  
  
> [!NOTE]  
>  Oracle FTP サイトが変更される可能性があるため、次の手順は完全に正確ではありません。  
  
### <a name="to-download-the-oracle-software-patches"></a>Oracle ソフトウェア修正プログラムをダウンロードするには  
  
1.  Oracle-ftp.oracle.com でパブリック FTP サイトに接続します。 ユーザー ID は "anonymous" で、パスワードは電子メールアドレスです。  
  
2.  次のディレクトリに移動します:/server/wgt_tech/Server/windowsnt。  
  
3.  Windows 95、Windows 98、および Windows NT/Windows 2000 に関連する修正プログラムをダウンロードするには、Oracle-7.3 または8.0 のバージョンのサブディレクトリに移動します。 2つのサブディレクトリは、/2 つのサブディレクトリです。  
  
4.  Oracle のネットワークテクノロジ (SQL * Net または Net8) の修正プログラムをダウンロードするには、次のディレクトリに移動します:/network。  
  
 この FTP サイトへのアクセスは、Web ブラウザーからは機能しない可能性があります。 問題が発生した場合は、"従来の" FTP クライアントを使用するか、DOS コマンドプロンプトを使用してください。  
  
> [!NOTE]  
>  Oracle は、現在のバージョンのバグを修正してから、ソフトウェア修正プログラムを使用して以前のバージョンに retrofits するため、利用可能な最新の修正プログラムをダウンロードすることをお勧めします。 これは、Oracle Server クライアントコンポーネントに特に当てはまります。 これらの修正プログラムのインストールについて不明な点がある場合は、Oracle サポートにお問い合わせください。
