## API Report File for "@backstage/plugin-search-backend-module-elasticsearch"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts
/// <reference types="node" />

import { ApiResponse } from '@opensearch-project/opensearch';
import { ApiResponse as ApiResponse_2 } from '@elastic/elasticsearch';
import { BatchSearchEngineIndexer } from '@backstage/plugin-search-backend-node';
import { BulkHelper } from '@opensearch-project/opensearch/lib/Helpers';
import { BulkStats } from '@opensearch-project/opensearch/lib/Helpers';
import { Config } from '@backstage/config';
import type { ConnectionOptions } from 'tls';
import { IndexableDocument } from '@backstage/plugin-search-common';
import { IndexableResultSet } from '@backstage/plugin-search-common';
import { Logger } from 'winston';
import { Readable } from 'stream';
import { SearchEngine } from '@backstage/plugin-search-common';
import { SearchQuery } from '@backstage/plugin-search-common';
import { TransportRequestPromise } from '@opensearch-project/opensearch/lib/Transport';
import { TransportRequestPromise as TransportRequestPromise_2 } from '@elastic/elasticsearch/lib/Transport';

// @public
export interface BaseElasticSearchClientOptions {
  // (undocumented)
  agent?: ElasticSearchAgentOptions | ((opts?: any) => unknown) | false;
  // (undocumented)
  compression?: 'gzip';
  // (undocumented)
  disablePrototypePoisoningProtection?: boolean | 'proto' | 'constructor';
  // (undocumented)
  enableMetaHeader?: boolean;
  // (undocumented)
  headers?: Record<string, any>;
  // (undocumented)
  maxRetries?: number;
  // (undocumented)
  name?: string | symbol;
  // (undocumented)
  nodeFilter?: (connection: any) => boolean;
  // (undocumented)
  nodeSelector?: ((connections: any[]) => any) | string;
  // (undocumented)
  opaqueIdPrefix?: string;
  // (undocumented)
  pingTimeout?: number;
  // (undocumented)
  proxy?: string | URL;
  // (undocumented)
  requestTimeout?: number;
  // (undocumented)
  resurrectStrategy?: 'ping' | 'optimistic' | 'none';
  // (undocumented)
  sniffEndpoint?: string;
  // (undocumented)
  sniffInterval?: number | boolean;
  // (undocumented)
  sniffOnConnectionFault?: boolean;
  // (undocumented)
  sniffOnStart?: boolean;
  // (undocumented)
  ssl?: ConnectionOptions;
  // (undocumented)
  suggestCompression?: boolean;
  // (undocumented)
  Transport?: ElasticSearchTransportConstructor;
}

// @public (undocumented)
export interface ElasticSearchAgentOptions {
  // (undocumented)
  keepAlive?: boolean;
  // (undocumented)
  keepAliveMsecs?: number;
  // (undocumented)
  maxFreeSockets?: number;
  // (undocumented)
  maxSockets?: number;
}

// @public (undocumented)
export type ElasticSearchAliasAction =
  | {
      remove: {
        index: any;
        alias: any;
      };
      add?: undefined;
    }
  | {
      add: {
        indices: any;
        alias: any;
        index?: undefined;
      };
      remove?: undefined;
    }
  | {
      add: {
        index: any;
        alias: any;
        indices?: undefined;
      };
      remove?: undefined;
    }
  | undefined;

// @public (undocumented)
export type ElasticSearchAuth =
  | OpenSearchAuth
  | {
      apiKey:
        | string
        | {
            id: string;
            api_key: string;
          };
    };

// @public
export type ElasticSearchClientOptions =
  | ElasticSearchElasticSearchClientOptions
  | OpenSearchElasticSearchClientOptions;

// @public
export class ElasticSearchClientWrapper {
  // (undocumented)
  bulk(bulkOptions: {
    datasource: Readable;
    onDocument: () => ElasticSearchIndexAction;
    refreshOnCompletion?: string | boolean;
  }): BulkHelper<BulkStats>;
  // (undocumented)
  createIndex({
    index,
  }: {
    index: string;
  }):
    | TransportRequestPromise<ApiResponse<Record<string, any>, unknown>>
    | TransportRequestPromise_2<ApiResponse_2<Record<string, any>, unknown>>;
  // (undocumented)
  deleteIndex({
    index,
  }: {
    index: string | string[];
  }):
    | TransportRequestPromise<ApiResponse<Record<string, any>, unknown>>
    | TransportRequestPromise_2<ApiResponse_2<Record<string, any>, unknown>>;
  // (undocumented)
  static fromClientOptions(
    options: ElasticSearchClientOptions,
  ): ElasticSearchClientWrapper;
  // (undocumented)
  getAliases({
    aliases,
  }: {
    aliases: string[];
  }):
    | TransportRequestPromise<ApiResponse<Record<string, any>, unknown>>
    | TransportRequestPromise_2<ApiResponse_2<Record<string, any>, unknown>>;
  // (undocumented)
  indexExists({
    index,
  }: {
    index: string | string[];
  }):
    | TransportRequestPromise<ApiResponse<boolean, unknown>>
    | TransportRequestPromise_2<ApiResponse_2<boolean, unknown>>;
  // (undocumented)
  putIndexTemplate(
    template: ElasticSearchCustomIndexTemplate,
  ):
    | TransportRequestPromise<ApiResponse<Record<string, any>, unknown>>
    | TransportRequestPromise_2<ApiResponse_2<Record<string, any>, unknown>>;
  // (undocumented)
  search({
    index,
    body,
  }: {
    index: string | string[];
    body: Object;
  }):
    | TransportRequestPromise<ApiResponse<Record<string, any>, unknown>>
    | TransportRequestPromise_2<ApiResponse_2<Record<string, any>, unknown>>;
  // (undocumented)
  updateAliases({
    actions,
  }: {
    actions: ElasticSearchAliasAction[];
  }):
    | TransportRequestPromise<ApiResponse<Record<string, any>, unknown>>
    | TransportRequestPromise_2<ApiResponse_2<Record<string, any>, unknown>>;
}

// @public
export type ElasticSearchConcreteQuery = {
  documentTypes?: string[];
  elasticSearchQuery: Object;
  pageSize: number;
};

// @public (undocumented)
export interface ElasticSearchConnectionConstructor {
  // (undocumented)
  new (opts?: any): any;
  // (undocumented)
  roles: {
    MASTER: string;
    DATA: string;
    INGEST: string;
    ML: string;
  };
  // (undocumented)
  statuses: {
    ALIVE: string;
    DEAD: string;
  };
}

// @public
export type ElasticSearchCustomIndexTemplate = {
  name: string;
  body: ElasticSearchCustomIndexTemplateBody;
};

// @public
export type ElasticSearchCustomIndexTemplateBody = {
  index_patterns: string[];
  composed_of?: string[];
  template?: Record<string, any>;
};

// @public
export interface ElasticSearchElasticSearchClientOptions
  extends BaseElasticSearchClientOptions {
  // (undocumented)
  auth?: ElasticSearchAuth;
  // (undocumented)
  cloud?: {
    id: string;
    username?: string;
    password?: string;
  };
  // (undocumented)
  Connection?: ElasticSearchConnectionConstructor;
  // (undocumented)
  node?:
    | string
    | string[]
    | ElasticSearchNodeOptions
    | ElasticSearchNodeOptions[];
  // (undocumented)
  nodes?:
    | string
    | string[]
    | ElasticSearchNodeOptions
    | ElasticSearchNodeOptions[];
  // (undocumented)
  provider?: 'elastic';
}

// @public (undocumented)
export type ElasticSearchHighlightConfig = {
  fragmentDelimiter: string;
  fragmentSize: number;
  numFragments: number;
  preTag: string;
  postTag: string;
};

// @public (undocumented)
export type ElasticSearchHighlightOptions = {
  fragmentDelimiter?: string;
  fragmentSize?: number;
  numFragments?: number;
};

// @public (undocumented)
export type ElasticSearchIndexAction = {
  index: {
    _index: string;
    [key: string]: any;
  };
};

// @public (undocumented)
export interface ElasticSearchNodeOptions {
  // (undocumented)
  agent?: ElasticSearchAgentOptions;
  // (undocumented)
  headers?: Record<string, any>;
  // (undocumented)
  id?: string;
  // (undocumented)
  roles?: {
    master: boolean;
    data: boolean;
    ingest: boolean;
    ml: boolean;
  };
  // (undocumented)
  ssl?: ConnectionOptions;
  // (undocumented)
  url: URL;
}

// @public
export type ElasticSearchOptions = {
  logger: Logger;
  config: Config;
  aliasPostfix?: string;
  indexPrefix?: string;
};

// @public
export type ElasticSearchQueryTranslator = (
  query: SearchQuery,
  options?: ElasticSearchQueryTranslatorOptions,
) => ElasticSearchConcreteQuery;

// @public
export type ElasticSearchQueryTranslatorOptions = {
  highlightOptions?: ElasticSearchHighlightConfig;
};

// @public (undocumented)
export class ElasticSearchSearchEngine implements SearchEngine {
  constructor(
    elasticSearchClientOptions: ElasticSearchClientOptions,
    aliasPostfix: string,
    indexPrefix: string,
    logger: Logger,
    highlightOptions?: ElasticSearchHighlightOptions,
  );
  // (undocumented)
  static fromConfig({
    logger,
    config,
    aliasPostfix,
    indexPrefix,
  }: ElasticSearchOptions): Promise<ElasticSearchSearchEngine>;
  // (undocumented)
  getIndexer(type: string): Promise<ElasticSearchSearchEngineIndexer>;
  newClient<T>(create: (options: ElasticSearchClientOptions) => T): T;
  // (undocumented)
  query(query: SearchQuery): Promise<IndexableResultSet>;
  // (undocumented)
  setIndexTemplate(template: ElasticSearchCustomIndexTemplate): Promise<void>;
  // (undocumented)
  setTranslator(translator: ElasticSearchQueryTranslator): void;
  // (undocumented)
  protected translator(
    query: SearchQuery,
    options?: ElasticSearchQueryTranslatorOptions,
  ): ElasticSearchConcreteQuery;
}

// @public
export class ElasticSearchSearchEngineIndexer extends BatchSearchEngineIndexer {
  constructor(options: ElasticSearchSearchEngineIndexerOptions);
  // (undocumented)
  finalize(): Promise<void>;
  // (undocumented)
  index(documents: IndexableDocument[]): Promise<void>;
  // (undocumented)
  readonly indexName: string;
  // (undocumented)
  initialize(): Promise<void>;
}

// @public
export type ElasticSearchSearchEngineIndexerOptions = {
  type: string;
  indexPrefix: string;
  indexSeparator: string;
  alias: string;
  logger: Logger;
  elasticSearchClientWrapper: ElasticSearchClientWrapper;
};

// @public (undocumented)
export interface ElasticSearchTransportConstructor {
  // (undocumented)
  new (opts?: any): any;
  // (undocumented)
  sniffReasons: {
    SNIFF_ON_START: string;
    SNIFF_INTERVAL: string;
    SNIFF_ON_CONNECTION_FAULT: string;
    DEFAULT: string;
  };
}

// @public
export const isOpenSearchCompatible: (
  opts: ElasticSearchClientOptions,
) => opts is OpenSearchElasticSearchClientOptions;

// @public (undocumented)
export type OpenSearchAuth = {
  username: string;
  password: string;
};

// @public (undocumented)
export interface OpenSearchConnectionConstructor {
  // (undocumented)
  new (opts?: any): any;
  // (undocumented)
  roles: {
    MASTER: string;
    DATA: string;
    INGEST: string;
  };
  // (undocumented)
  statuses: {
    ALIVE: string;
    DEAD: string;
  };
}

// @public
export interface OpenSearchElasticSearchClientOptions
  extends BaseElasticSearchClientOptions {
  // (undocumented)
  auth?: OpenSearchAuth;
  // (undocumented)
  connection?: OpenSearchConnectionConstructor;
  // (undocumented)
  node?: string | string[] | OpenSearchNodeOptions | OpenSearchNodeOptions[];
  // (undocumented)
  nodes?: string | string[] | OpenSearchNodeOptions | OpenSearchNodeOptions[];
  // (undocumented)
  provider?: 'aws';
}

// @public (undocumented)
export interface OpenSearchNodeOptions {
  // (undocumented)
  agent?: ElasticSearchAgentOptions;
  // (undocumented)
  headers?: Record<string, any>;
  // (undocumented)
  id?: string;
  // (undocumented)
  roles?: {
    master: boolean;
    data: boolean;
    ingest: boolean;
  };
  // (undocumented)
  ssl?: ConnectionOptions;
  // (undocumented)
  url: URL;
}
```
