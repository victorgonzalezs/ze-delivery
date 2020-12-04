html cadastro 

<app-pesquisa></app-pesquisa>
<mat-divider></mat-divider>
<app-precadastro></app-precadastro>
<mat-divider></mat-divider>
<app-cadastrados></app-cadastrados>



app.modules 

import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { BrowserAnimationsModule } from '@angular/platform-browser/animations';
import { HomeComponent } from './views/home/home.component';
import { CadastroComponent } from './views/cadastro/cadastro.component';
import { ConciliacaoComponent } from './views/conciliacao/conciliacao.component';
import { ImComponent } from './views/im/im.component';
import { MatTableModule } from '@angular/material/table';
import { PesquisaComponent } from './views/cadastro/pesquisa/pesquisa.component';
import { PrecadastroComponent } from './views/cadastro/precadastro/precadastro.component';
import { CadastradosComponent } from './views/cadastro/cadastrados/cadastrados.component';
import { MatPaginatorModule } from '@angular/material/paginator';
import { MatFormFieldModule } from '@angular/material/form-field';
import { MatInputModule } from '@angular/material/input';
import { MatIconModule } from '@angular/material/icon';
import { MatDividerModule } from '@angular/material/divider';
import { MatToolbarModule } from '@angular/material/toolbar';
import { MatButtonModule } from '@angular/material/button';
import {MatDialogModule} from '@angular/material/dialog';

@NgModule({
  declarations: [
    AppComponent,
    HomeComponent,
    CadastroComponent,
    ConciliacaoComponent,
    ImComponent,
    PesquisaComponent,
    PrecadastroComponent,
    CadastradosComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    BrowserAnimationsModule,
    MatTableModule,
    MatPaginatorModule,
    MatFormFieldModule,
    MatInputModule,
    MatIconModule,
    MatDividerModule,
    MatToolbarModule,
    MatButtonModule,
    MatDialogModule

  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
