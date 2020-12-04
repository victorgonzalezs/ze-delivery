import { EventListenerFocusTrapInertStrategy } from '@angular/cdk/a11y';
import { AfterViewInit, Component, ViewChild } from '@angular/core';
import { MatPaginator } from '@angular/material/paginator';
import { MatSort } from '@angular/material/sort';
import { MatTableDataSource } from '@angular/material/table';

export interface UserData {
  nome: string;
  farol: string;
  farol_color: string;
  status: string;
  inscricao: string;
  agentes: number;
  data: string;

}

const NAMES: string[] = [
  'IACO AGRICOLA SA', 'ENGIE GERACAO SOLAR DISTRIBUIDA SA', 'ELETRON RESISTENCIAS LTDA', 'ENGIE AXIMA DO BRASIL INSTALACAO DE AR CONDICIONADO E REFRIGERACAO LTDA', 'A.W. FABER CASTELL S.A.', 'ENGIE GERACAO DE ENERGIA FOTOVOLTAICA LTDA', 'ENGIE BRASIL ENERGIA SA', 'ENGIE BRASIL ENERGIA SA', 'CPFL GERACAO DE ENERGIA S A', 'CPFL BIOENERGIA SA', 'CPFL BIO PEDRA LTDA', 'CPFL SUL CENTRAIS ELETRICAS LTDA', 'CPFL BIO ESTER LTDA', 'ELETRON POWER GERACAO E COMERCIALIZADORA DE ENERGIA LTDA', 'ADECOAGRO ENERGIA LTDA', 'AES TIETE ENERGIA AS', 'ENGIE TRANSMISSAO DE ENERGIA LTDA', 'CPFL TRANSMISSAO PIRACICABA SA', 'ENGIE TRADING COMERCIALIZADORA DE ENERGIA LTDA'
];
const CNPJ: string[] = [
  '07.895.728/0001-78', '24.564.686/0001-01', '53.565.370/0001-32', '17.394.332/0001-09', '59.596.908/0001-52', '09.265.443/0001-89', '02.474.103/0002-08', '02.474.103/0001-19', '03.953.509/0001-47', '07.693.890/0001-03', '11.631.6800001-68', '05.441.551/0001-04', '14.205.729/0001-09', '27.708.608/0001-21', '21.228.540/0001-05', '04.128.563/0001-10', '27.093.940/0001-29', '17.079.395/0001-62', '31.635.668/0001-39'
];
const STATUS: string[] = [
  'ATIVO', 'ATIVO', 'ATIVO', 'ATIVO', 'ATIVO', 'ATIVO', 'BLOQUEADO', 'ATIVO', 'ATIVO', 'ATIVO', 'ATIVO', 'ATIVO', 'ATIVO', 'ATIVO', 'ATIVO', 'ATIVO', 'ATIVO', 'ATIVO', 'ATIVO'
];
const FAROL: string[] = [
  'OK', 'NOK', 'WAIT'
];

@Component({
  selector: 'app-cadastrados',
  templateUrl: './cadastrados.component.html',
  styleUrls: ['./cadastrados.component.css']
})
export class CadastradosComponent implements AfterViewInit {
  displayedColumns: string[] = ['farol', 'nome', 'inscricao', 'agentes', 'status', 'data'];
  dataSource: MatTableDataSource<UserData>;

  @ViewChild(MatPaginator) paginator: MatPaginator;
  @ViewChild(MatSort) sort: MatSort;

  constructor() {
    // Create 100 users
    const users = Array.from({ length: 100 }, (_, k) => createNewUser(k + 1));

    // Assign the data to the data source for the table to render
    this.dataSource = new MatTableDataSource(users);
  }

  ngAfterViewInit() {
    this.dataSource.paginator = this.paginator;
    this.dataSource.sort = this.sort;
  }

  applyFilter(event: Event) {
    const filterValue = (event.target as HTMLInputElement).value;
    this.dataSource.filter = filterValue.trim().toLowerCase();

    if (this.dataSource.paginator) {
      this.dataSource.paginator.firstPage();
    }
  }
}

/** Builds and returns a new User. */
function createNewUser(id: number): UserData {
  const name = NAMES[Math.round(Math.random() * (NAMES.length - 1))];
  const status = STATUS[Math.round(Math.random() * (STATUS.length - 1))];
  const cnpj = CNPJ[Math.round(Math.random() * (CNPJ.length - 1))];
  const farol = FAROL[Math.round(Math.random() * (FAROL.length - 1))];

  return {
    nome: name,
    farol: getFarolIcon(farol),
    farol_color: getFarolColor(farol),
    status: status,
    inscricao: cnpj,
    agentes: getRandomInt(1, 10),
    data: '15/10/2020',
  };
}

function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min)) + min;
}
function getFarolIcon(status_farol) {
  if (status_farol === 'OK') {
    return 'check_circle'
  } else if (status_farol === 'NOK') {
    return 'error';
  } else {
    return 'watch_later';
  }
}


function getFarolColor(status_farol) {
  if (status_farol === 'OK') {
    return 'green'
  } else if (status_farol === 'NOK') {
    return 'red';
  } else {
    return 'yellow';
  }
}
