import { Component, OnInit } from '@angular/core';
import { FormsModule }   from '@angular/forms';
import { CommonModule } from '@angular/common';

@Component({
  selector: 'app-pesquisa',
  templateUrl: './pesquisa.component.html',
  styleUrls: ['./pesquisa.component.css']
})


@NgModule({
  imports: [
    CommonModule,
    FormsModule // Adicionei aqui
  ]
})

export class PesquisaComponent implements OnInit {

  constructor() { }

  ngOnInit(): void {
  }
  value = 'Clear me';
}
