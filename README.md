pokazivac.h
===========
struct pacijent{
	char ime[15],prezime[15],spol[2];
	int dan,mjesec,godina;
	int ai,bi,ci,di,ei;
};
struct el{
	pacijent element;
	el *sljedeci;
};
struct red{
	el *celo,*zacelje;
	red(){}
};
red *InitQ(red *Q){
	el *novi=new el;
	Q = new red;
	novi->sljedeci=NULL;
	Q->celo=novi;
	Q->zacelje=novi;
	return Q;
}
pacijent FrontQ(red *Q){
	return Q->celo->sljedeci->element;
}
void EnQueueQ(pacijent x,red *Q){
	el *novi=new el;
	novi->element=x;
	novi->sljedeci=NULL;
	Q->zacelje->sljedeci=novi;
	Q->zacelje=novi;
}
void DeQueueQ(red *Q){
	el *brisi=Q->celo;
	Q->celo=brisi->sljedeci;
	delete brisi;
}
bool IsEmptyQ(red *Q){
	if(Q->celo==Q->zacelje)return true;
	return false;
}
